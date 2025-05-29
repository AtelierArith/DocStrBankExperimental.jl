```julia
download_jlcall(; ...) -> String
download_jlcall(filename::String; latest, force) -> String

```

`jlcall.m` MATLAB API 関数をファイル `filename` にダウンロードまたはコピーします。

デフォルトでは、`jlcall.m` はインストールされた `MATDaemon.jl` ソースツリーの `api` サブフォルダーから現在の作業ディレクトリにコピーされます。最新のバージョンの `jlcall.m` は、`latest = true` を渡すことで GitHub からダウンロードできます。宛先 `filename` は、`force = true` を渡すことで既存のものを上書きできます。
