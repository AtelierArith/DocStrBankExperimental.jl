```
AreaGpBasisFns(line_gp_fns1::LineGpBasisFns, line_gp_fns2::LineGpBasisFns)
```

メッシュ領域内のすべてのガウス点での2次元Bスプライン基底関数とその導関数。

渡された2つの[`LineGpBasisFns`](@ref)構造体、`line_gp_fns1`と`line_gp_fns2`は、それぞれ$ζ^1$および$ζ^2$方向の1次元導関数を含んでいます。表面上のBスプラインのテンソル積構造により[piegl-tiller](@citep)、2次元基底関数とその導関数を計算することは簡単です。[`LineGpBasisFns`](@ref)の場合と同様に、要素からユニークな要素へのマッピングが生成され、ユニークな基底関数の計算のみが保存されます。この構造体には3つのフィールドがあります：

  * `nel` –> 面積要素の数
  * `uel_ids` –> `elem_id`から`unique_elem_id`へのマッピング
  * `ufns` –> タイプ[`GpBasisFnsζα`](@ref)のユニークな2次元基底関数の`num_unique_elems`×`ngp`行列
