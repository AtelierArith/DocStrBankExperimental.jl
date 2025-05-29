`N` 個のチェビシェフ-ガウス-ロバット（チェビシェフの極値）を計算し、`domain` で指定された区間にポイントをスケーリングします（デフォルトは [1.0,-1.0]）。指定されたドメインに位置する `N` ポイントを含むベクトルを返します。

チェビシェフ-ガウス-ロバットポイントは、スモリャク近似がチェビシェフ多項式に基づいている場合に使用されます。

# シグネチャ

points = chebyshev*gauss*lobatto(N,domain) points = chebyshev_extrema(N,domain)

# 例

```
julia> points = chebyshev_gauss_lobatto(4)
[-1.0
 -0.5000000000000001
  0.5000000000000001
  1.0]

julia> points = chebyshev_gauss_lobatto(4,[3.0,-1.0])
[-1.0
 -2.220446049250313e-16
  2.0
  3.0]
```
