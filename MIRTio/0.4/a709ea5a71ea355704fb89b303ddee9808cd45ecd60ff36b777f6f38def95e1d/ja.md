```
dat = loadrds(fid::IOStream, frame::Int, frsize::Int, ncoil::Int; 
              T::Type{<:Union{Int16,Int32}} = Int16)
```

GEのRaw Data Serverで作成されたMRIデータファイルから1ショット（フレーム）をロードします。

入力

  * `fid::IOStream` ファイルハンドル
  * `frame::Int` ショット/フレーム番号
  * `frsize::Int` 各リードアウトのデータポイント数（コイルごと）
  * `ncoil::Int` 受信コイルの数

オプション

  * `T::Type{<:Union{Int16,Int32}} = Int16` ロードされる（複素）データの基本型

出力

  * `dat::Array{Complex{T}}` `[frsize, ncoil]`
