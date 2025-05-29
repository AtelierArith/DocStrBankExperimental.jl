```
correlation_matrix(psi::MPS,
                   Op1::AbstractString,
                   Op2::AbstractString;
                   kwargs...)

correlation_matrix(psi::MPS,
                   Op1::Matrix{<:Number},
                   Op2::Matrix{<:Number};
                   kwargs...)
```

MPS psiと2つの文字列（`op`関数によって認識される演算子を示す）を与えると、効率的なMPS技術を使用して2点相関関数行列C[i,j] = <psi| Op1i Op2j |psi>を計算します。行列Cを返します。

# オプションのキーワード引数

  * `sites = 1:length(psi)`：指定された範囲内のサイトに対してのみ相関を計算します
  * `ishermitian = false` : `false`の場合、対角線の上と下の行列要素の独立した計算を強制しますが、`true`の場合はそれらが複素共役であると仮定します。

サイズNxNの相関行列と典型的なボンド次元mのMPSに対して、このアルゴリズムのスケーリングはN^2*m^3です。

# 例

```julia
N = 30
m = 4

s = siteinds("S=1/2", N)
psi = random_mps(s; linkdims=m)
Czz = correlation_matrix(psi, "Sz", "Sz")
Czz = correlation_matrix(psi, [1/2 0; 0 -1/2], [1/2 0; 0 -1/2]) # 上と同じ

s = siteinds("Electron", N; conserve_qns=true)
psi = random_mps(s, n -> isodd(n) ? "Up" : "Dn"; linkdims=m)
Cuu = correlation_matrix(psi, "Cdagup", "Cup"; sites=2:8)
```
