```
StoreCallbacks{V} <: AriannaAlgorithm
```

シミュレーション中にコールバック値を保存するアルゴリズム。

# フィールド

  * `callbacks::V`: 評価するコールバック関数のベクター
  * `paths::Vector{String}`: 各コールバックの出力ファイルへのパス
  * `files::Vector{IOStream}`: コールバック値を書き込むためのファイルハンドル
  * `store_first::Bool`: 初期化時にコールバック値を保存するかどうか
  * `store_last::Bool`: 終了時にコールバック値を保存するかどうか

# コンストラクタ

```
StoreCallbacks(callbacks::V, path; store_first::Bool=true, store_last::Bool=false)
```

新しいStoreCallbacksインスタンスを作成します。

# 引数

  * `callbacks::V`: コールバック関数のベクター
  * `path`: 出力ファイルのベースパス
  * `store_first=true`: 初期化時に値を保存する
  * `store_last=false`: 終了時に値を保存する
