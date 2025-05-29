```
s3open(s3_url::AbstractString, mode::AbstractString="rb") -> file, io
```

S3 URLからファイルを開きます。

## 入力引数

  * `s3_url::AbstractString`: ファイルのS3 URL。
  * `mode::AbstractString="rb"`: アクセスモード。デフォルトはバイナリモードの読み取り専用です。

## 出力引数

  * `file`: ファイルのようなNWBオブジェクト
  * `io`: ファイルへのioストリーム。これはJuliaを終了する前に`io.close()`されるべきです。

## 例

```julia
s3_url = "https://visual-behavior-neuropixels-data.s3.us-west-2.amazonaws.com/visual-behavior-neuropixels/behavior_ecephys_sessions/1044385384/ecephys_session_1044385384.nwb"
data = s3open(s3_url)
```
