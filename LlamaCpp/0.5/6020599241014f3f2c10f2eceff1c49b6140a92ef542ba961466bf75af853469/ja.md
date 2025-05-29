```
download_model(url::AbstractString; dir::AbstractString="models")
```

指定された `url` から HuggingFace Hub にあるモデルを `dir` ディレクトリにダウンロードし、ダウンロードしたファイルへの `model_path` を返します。`dir` ディレクトリが存在しない場合は、作成されます。

注意: 現在、GGUF形式のモデルのみが許可されています（URLは `.gguf` で終わる必要があります）。

利用可能なモデルのリストについては、[HuggingFace Model Hub](https://huggingface.co/models) を参照してください。

# 例

```julia
# Rocketモデルをダウンロードする (~1GB)
url = "https://huggingface.co/ikawrakow/various-2bit-sota-gguf/resolve/main/rocket-3b-2.76bpw.gguf"
model = download_model(url) 
# 出力: "models/rocket-3b-2.76bpw.gguf"
```
