**Hola estamos en la clas de anajuahc** 

 - 1 uno
 - 2 dos
 - 3 tres
 - 4

    def fetch_commenters(issue_url, api_key):
        api_url = issue_url.replace('github.com', 'api.github.com/repos') + '/comments'
        headers = {'Authorization': f'token {api_key}'}
        response = requests.get(api_url, headers=headers)
        
        if response.status_code == 200:
            comments = response.json()
            usernames = [comment['user']['login'] for comment in comments]
            
            # Convert to set to remove duplicates, then convert back to list
            usernames = list(set(usernames))
            
            usernames_str = ', '.join(usernames)
            return usernames_str
        else:
            print(f'Failed to fetch comments: {response.status_code}')
            return None
    
    issue_url = 'https://github.com/lasr21/eventos_/issues/2'
    api_key = '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'
    usernames = fetch_commenters(issue_url, api_key)
    print(usernames)
