```
sharefolder(client::PCloudClient; kwargs...)
```

Shares a folder with another user.

Share may be subject to confirmation from the other user. The folder to be shared is identified by `folderid` or `path`.

Optional share `name` can be provided, if it is not, the folder name is used as sharename. Implementations are advised to give opportunity to the sharing user to select the share `name`, which should be pre-filled with the folder name.

The required parameter `mail` holds the email address of the user with whom you are sharing the folder.

The required parameter `permissions` sets the permissions for the folder.

Zero for read-only or any combination (sum/or) of

  * `1`: Create permission
  * `2`: Modify permission
  * `4`: Delete permission

Optional parameter `message` allows adding a message to pass to the receiving user.

Folder sharing is a complicated operation and the following errors are likely to be returned:- `2014`: the user's address is not verified. Implementations are advised upon user confirmation to call sendverificationemail and to ask the user to check his/her email.

  * `2015`: root folder cannot be shared, this check SHOULD also be performed on the client.
  * `2016::ismine`: one can only share folders with set to true, implementations SHOULD check this locally too.
  * `2017`: user does not accept requests from you or from anybody, implementations can not know if this is going to happen, but are expected to act appropriately on this error.

Source: https://docs.pcloud.com/methods/sharing/sharefolder.html

# Arguments

  * `folderid::Int`: folder id of the shared folder
  * `path::String`: path to the shared folder
  * `mail::String`: mail of the user with whom you are sharing the folder
  * `permissions::Int`: bitwise combination of permission flags

Use `path` or `folderid`

# Optional Arguments

  * `name::String`: name of the share. Default - the folder name.
  * `message::String`: message to pass to the receiving user.

# Output Example

```
{
    result: 0
}
```
