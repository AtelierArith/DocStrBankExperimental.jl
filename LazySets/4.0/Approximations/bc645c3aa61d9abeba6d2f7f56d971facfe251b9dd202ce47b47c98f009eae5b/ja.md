```
underapproximate(P::AbstractPolyhedron{N}, ::Type{Ellipsoid};
                 backend=default_sdp_solver(),
                 interior_point::AbstractVector{N}=chebyshev_center_radius(P)[1]
                ) where {N<:Real}
```

ポリヘドラル集合を最大体積の楕円体で下近似します。

### 入力

  * `P`         – ポリヘドラル集合
  * `Ellipsoid` – ディスパッチ用の型
  * `backend`   – （オプション、デフォルト: `default_sdp_solver()`）半正定値プログラムを解くためのバックエンド
  * `interior_point` – （オプション、デフォルト: `chebyshev_center_radius(P)[1]`）楕円体の内部点（アルゴリズムに必要: 詳細は以下を参照）

### 出力

$$
E ⊆ P
$$

となる楕円体 $E$。$P$ が有界であれば、$E$ は最大体積を持ちます（$P$ が無限大の方向にある場合はそのような保証はありません）。

### 注意事項

最大体積の楕円体は *Löwner-John ellipsoid* とも呼ばれます。

アルゴリズムでは、楕円体の内部にある点を指定する必要があり、これは引数 `interior_point` で指定できます。もしそのような点が知られていない場合（すなわち、`interior_point == nothing`）、実装はチェビシェフ中心を計算します（[`chebyshev_center_radius`](@ref) を参照）。

チェビシェフ中心はデフォルトのLPソルバーを使用して計算され、渡されたSDPソルバー `backend` は使用されません（`backend` がLPをサポートする保証がないため）。カスタムLPソルバーを使用する必要がある場合は、チェビシェフ中心を手動で計算し、渡す必要があります。

### アルゴリズム

問題を直接エンコードするために、パッケージ [`SetProg.jl`](https://github.com/blegat/SetProg.jl/) を使用します。

アルゴリズムの説明は [こちら](https://systemanalysisdpt-cmc-msu.github.io/ellipsoids/doc/chap_ellcalc.html#maximum-volume-ellipsoids) にあります。
