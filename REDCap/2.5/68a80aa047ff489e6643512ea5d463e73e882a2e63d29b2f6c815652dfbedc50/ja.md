function import*file*from*file*repository(; url=get*url(), token=get*token(), format=nothing, file, folder_id=nothing,)

Export a list of files for all subfolders function import*file*from*file*repository(; url=get*url(), token=get*token(), format=nothing, returnFormat=nothing, name=nothing, file=nothing, folder_id=nothing,)

# Named arguments

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取られます)
  * `token`: REDCap プロジェクトおよびユーザー名に特有の API トークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取られます)
  * `file`: 新しいファイルの内容
  * `folder_id`: 対象フォルダの folder_id (デフォルトはファイルリポジトリの最上位ディレクトリ)
  * `format`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
