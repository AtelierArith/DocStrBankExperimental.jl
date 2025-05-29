```
create_hcurl_basis(c::Ceed, topo::Topology, ncomp, nnodes, nqpts, interp, curl, qref, qweight)
```

H(curl) 離散化のための非テンソル積基底を作成します

# 引数:

  * `ceed`:    [`Ceed`](@ref) オブジェクトで、[`Basis`](@ref) が作成されます。
  * `topo`:    要素の [`Topology`](@ref)、例えばハイパーキューブ、単体など。
  * `ncomp`:   フィールドコンポーネントの数（スカラー場の場合は 1）。
  * `nnodes`:  ノードの総数。
  * `nqpts`:   積分点の総数。
  * `interp`:  積分点での基底関数の値を表すサイズ `(dim, nqpts, nnodes)` の行列。
  * `curl`:    積分点での基底関数のカールを表すサイズ `(curlcomp, nqpts, nnodes)` の行列（`curlcomp = 1 if dim < 3 else dim`）。
  * `qref`:    参照要素 $[-1, 1]$ 上の積分点の位置を保持するサイズ `(dim, nqpts)` の行列。
  * `qweight`: 参照要素上の積分重みを保持する長さ `nqpts` の配列。
