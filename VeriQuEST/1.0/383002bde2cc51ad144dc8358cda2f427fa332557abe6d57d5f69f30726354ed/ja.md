```
run_mbqc(para)
```

指定されたパラメータを使用して、測定に基づく量子計算（MBQC）を実行します。この関数は、UBQCリソースを作成し、クライアントメタグラフを生成し、クライアントメタグラフから量子状態を抽出し、計算を実行し、出力を取得します。

# 引数

  * `para`: MBQCのためのパラメータを含むNamedTuple。

# 戻り値

  * `get_output`を呼び出すことによって得られるMBQCの出力。

# 例

```julia
para = (args)::NamedTuple # 関数特有の引数
mbqc_output = run_mbqc(para)
```
