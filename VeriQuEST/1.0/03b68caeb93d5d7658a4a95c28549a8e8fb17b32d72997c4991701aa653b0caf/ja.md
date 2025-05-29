```
run_ubqc(para)
```

提供されたパラメータを使用して、ユニバーサルブラインド量子計算（UBQC）を実行します。この関数は、UBQCリソースを作成し、クライアントメタグラフを生成し、クライアントからグラフと量子レジスタ（qureg）を抽出し、サーバーリソースを作成し、計算を実行し、UBQC出力を取得します。

# 引数

  * `para`: UBQCのパラメータを含む辞書。`：state_type`というキーを含む必要があります。

# 戻り値

  * `get_ubqc_output`を呼び出すことによって得られるUBQCの出力。

# 例

```julia
para = (args)::NamedTuple # 関数特有の引数
ubqc_output = run_ubqc(para)
```
