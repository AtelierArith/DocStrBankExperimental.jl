# MIMEFileExtensions

ファイル拡張子からMIMEタイプを検索し、その逆も行います。

これはApache HTTPサーバープロジェクトのマッピングに基づいています: https://svn.apache.org/repos/asf/httpd/httpd/trunk/docs/conf/mime.types

## 例

```jldoctest README
julia> using MIMEFileExtensions

julia> fileexts_from_mime("image/jpeg")
3-element Vector{Symbol}:
 :jpeg
 :jpg
 :jpe

julia> mimes_from_fileext("txt")
1-element Vector{Symbol}:
 Symbol("text/plain")
```

## 参照

  * https://github.com/fonsp/MIMEs.jl: より包括的なデータベースに基づいた類似のパッケージ。
  * https://github.com/JuliaIO/FileType.jl: ファイルの内容に基づいてファイルタイプ（MIMEを含む）を検出します。
