```
get_ubqc_output(::Client, ::ComputationRound, mg::MetaGraphs.MetaGraph)
```

クライアントのメタグラフから計算ラウンドの出力を取得します。この関数は、メタグラフのラウンドタイプが `TestRound` であるかどうかをチェックし、そうであればエラーをスローします。そうでなければ、計算ラウンドの出力を取得して返します。

# 引数

  * `::Client`: `Client` インスタンス。
  * `::ComputationRound`: `ComputationRound` インスタンス。
  * `mg::MetaGraphs.MetaGraph`: クライアントのメタグラフ。

# 戻り値

  * 計算ラウンドの出力。

# エラー

  * メタグラフのラウンドタイプが `TestRound` の場合、エラーをスローします。

# 例

```julia
ubqc_output = get_ubqc_output(Client(), ComputationRound(), mg)
```
