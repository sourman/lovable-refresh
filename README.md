# Lovable.dev Repository Replacement Guide

## Problem
Lovable.dev creates a new GitHub repository for each project and does not support attaching to existing repositories. This guide explains how to replace a newly created Lovable.dev repository with an existing one.

## Solution
1. **Rename the Existing Repository**:
   - Go to GitHub and rename the existing repository to `old-project-name`.

2. **Create a New Lovable.dev Project**:
   - Start a new project in Lovable.dev.
   - Integrate it with GitHub, using the original repository name (e.g., `project-name`).

3. **Delete the Newly Created Repository**:
   - Use the GitHub App to delete the repository created by Lovable.dev.

4. **Push Existing Content**:
   - Clone the `old-project-name` repository locally.
   - Change the remote URL to point to the new Lovable.dev repository (`project-name`).
   - Push all branches and tags to the new repository.

5. **Cleanup**:
   - Delete the `old-project-name` repository if no longer needed.

## GitHub App Setup
1. Create a GitHub App with the following permissions:
   - `repo` (full control)
   - `delete_repo`
2. Install the app on your friend's GitHub account.

## Automation Script (Optional)
Use the GitHub API to automate steps 3 and 4:
```bash
# Delete the new repository
curl -X DELETE -H "Authorization: token YOUR_TOKEN" https://api.github.com/repos/username/project-name

# Push existing content
git remote set-url origin https://github.com/username/project-name.git
git push --all
```

## Notes
- Ensure the GitHub App has the necessary permissions before running the script.
- Backup the existing repository before making changes.
