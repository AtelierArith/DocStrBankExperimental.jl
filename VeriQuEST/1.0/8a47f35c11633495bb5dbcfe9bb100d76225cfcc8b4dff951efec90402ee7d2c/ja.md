```
run_verification_simulator(::TrustworthyServer, ::Terse, para)
```

信頼できるサーバーのための検証シミュレーターをテレースモードで実行します。この関数は色付けを定義し、逆流を計算し、クライアントリソースを作成し、ランダムなラウンドを描画し、検証を実行し、ラウンドを検証し、モード出力を取得し、検証結果とモードの結果を返します。

# 引数

  * `::TrustworthyServer`: `TrustworthyServer`のインスタンス。
  * `::Terse`: `Terse`のインスタンス。
  * `para`: 検証シミュレーターのパラメータを含む辞書。`：graph`、`：input`、`：output`、`：secret_angles`、`：forward_flow`、`：total_rounds`、および`：computation_rounds`のキーを含む必要があります。

# 戻り値

  * テスト検証結果、計算検証結果、およびモードの結果を含むタプル。

# 例

```julia
para = (args)::NamedTuple # 関数特有の引数
result = run_verification_simulator(TrustworthyServer(), Terse(), para)
```
