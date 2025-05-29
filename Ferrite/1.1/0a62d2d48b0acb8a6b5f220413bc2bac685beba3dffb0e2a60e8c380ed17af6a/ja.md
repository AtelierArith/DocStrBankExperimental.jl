```
apply_analytical!(
    a::AbstractVector, dh::AbstractDofHandler, fieldname::Symbol,
    f::Function, cellset=1:getncells(get_grid(dh)))
```

解を `f(x)` として適用し、フィールド `fieldname` に関連する自由度ベクトル `a` の値をすべてのセル `cellset` に対して修正します。関数 `f(x)` は自由度の空間座標を与えられます。スカラー場の場合、`f(x)::Number`、および次元 `dim` のベクトル場の場合、`f(x)::Vec{dim}` です。

この関数は、時間依存問題の初期条件を適用するために使用できます。

!!! note
    この関数は、(代数的) ノードでの関数値が対応する自由度値と等しい場合にのみ、標準的なノード有限要素補間に対して機能します。これは、ラグランジュ補間やセレンディピティ補間、サブパラメトリックおよびスーパーパラメトリック要素を含む場合に当てはまります。

