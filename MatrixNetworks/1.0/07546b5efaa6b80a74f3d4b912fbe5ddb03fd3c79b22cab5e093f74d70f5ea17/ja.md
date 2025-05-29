# `chung_lu_undirected`

近似無向Chung-Luグラフを生成します。近似である理由は、|E|エッジを正確に描画し、各エッジがChung-Luモデルからサンプリングされるためです。しかし、その後、重複エッジと自己ループを破棄します。したがって、新しいグラフは常に入力次数列よりも少ないエッジを持ちます。

**これは将来のバージョンで変更され、正確なChung-Luモデルを提供する可能性があります。**

グラフが

## 使用法

  * `chung_lu_undirected(d)`
  * `chung_lu_undirected(d,nedges)`

## 入力

  * `d`: 次数列ベクトル。このベクトルは非負であり、各頂点の期待される次数を持っています。

## 出力

  * Chung-Luサンプルから得られる無向グラフのMatrixNetwork。

## 例

```
A = load_matrix_network("tapir")
d = vec(sum(A,1))
B = sparse(chung_lu_undirected(d))
nnz(A)
nnz(B)
```
