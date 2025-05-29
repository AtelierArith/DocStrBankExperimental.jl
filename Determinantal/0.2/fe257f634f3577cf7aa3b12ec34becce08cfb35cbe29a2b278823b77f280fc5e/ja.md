```
polyfeatures(x,order)
```

特定の次数までのモノミアル特徴を計算します。たとえば、入力が ℝ² のベクトルで構成されている場合、次数 ≤ 2 のモノミアルは 1,x₁,x₂,x₁x₂,x₁²,x₂² です。次数 r のモノミアルの数は次のように表されます：${ d+r \choose r}$

入力点が d > 1 の場合、入力 x が d * n か n * d かを ColVecs または RowVecs を使用して示してください。

出力は行に沿って点があり、列に沿ってモノミアルがあります。

## 例

```
x = randn(2,10) #次元 2 の 10 点
polyfeatures(ColVecs(x),2) #出力は 10 行と 6 列
polyfeatures(RowVecs(x),2) #出力は 2 行と 66 列
```
