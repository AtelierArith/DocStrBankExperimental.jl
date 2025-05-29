function import*file*from*file*repository(; url=get*url(), token=get*token(), format=nothing, file, folder_id=nothing,)

Export a list of files for all subfolders function import*file*from*file*repository(; url=get*url(), token=get*token(), format=nothing, returnFormat=nothing, name=nothing, file=nothing, folder_id=nothing,)

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `file`: contents of the new file
  * `folder_id`: folder_id of intended folder (default is the top-level directory of the File Repository)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
