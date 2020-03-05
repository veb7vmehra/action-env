Action of Creating Env file.
Name: veb7vmehra/action-env

Github Action to create a .env file with Github Secrets

Usage
The action looks for environment variables that start with INPUT_ENVKEY_ and creates an envfile with them. To add a key to the envfile, add a key/pair to the with: section. It must begin with envkey_.

name: action-env

on: [push]

jobs:

  action-env:
 
    runs-on: ubuntu-18.04
 
    steps:
    - name: action-env
      uses: veb7vmehra/action-env
      with:
        envkey_DEBUG: false
        envkey_SOME_API_KEY: "123456abcdef"
        envkey_SECRET_KEY: ${{ secrets.SECRET_KEY }}
        some_other_variable: foobar
        file_name: .env
In this example, there are 4 keys:

envkey_DEBUG, envkey_SOME_API_KEY - String values

envkey_SECRET_KEY - A secret stored in the repository's Github Secrets

some_other_variable - Won't be used because it doesn't start with envkey_

file_name - Optional. Set the name of the output envfile. Defaults to .env