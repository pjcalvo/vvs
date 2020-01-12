api for UnCompa.com

# Tech Stack
    * Python3
    * Flask
    * MySql

# Running
```bash
python 3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
FLASK_APP=api/run.py flask run #dev server
or
gunicorn api.run:app  #production server
```

**To use configuration:**
```bash
export FLASK_ENV=development
export FLASK_ENV=production
```

**Code Style Check:**
Using Pep8 for coding standards and code styling. For custom config setup .pycodestyle
```bash
pycodestyle api/* --.pycodestyle
```

**Codecoverage:**
Suggested codecoverage above 90%. `.coveragerc` stores the configuration for the pytest-cov execution
```bash
pytest --cov-config=.coveragerc --cov=api/
```

**Secrets**
Secrets are not committed but can be readed as a setting file, for DB passwords and so use the .secrets file

# Continues integration and deployment 
**Bitbucket pipelines**
- Master branch is locked and no direct commits are allowed
- When a new PR is created a bitbucket pipeline is executed to measure coverage, codestyle and unit tests.
- If the build is succesful it can be merged to master.
- After merging to master another pipeline is executed to make sure the merge was succesful.

**Deployment to heroku**
Once the master build has finished testing,  a manual triggered will be waiting to deploy to heroku.
- This will allow us to deploy on demand and skip configuration, miscelaneus or undesired deployments to staging.
- To deploy live go to Heroku pipelines and promote the latest build on staging

# Contribution Guidelines
Please follow the team rules:
    * No commits to Master
    * Meaningful descriptive Pull Requests: *[ISSUE-001] Nice PR description*
    * Continues integration: [ISSUE-001] *This is a small nice commit*

# Contributors
    * Alejandro Sanchez
    * Gabriel Calvo
    * Pablo Calvo

