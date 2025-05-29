```
A = JopDwt(T, n...[, wt=wavelet(WT.haar, WT.Lifting)])
```

`A` は N-D (N=1,2 または 3) ウェーブレット変換演算子で、型 `T` のドメインと次元 `n` に作用します。オプション引数 `wt` はウェーブレットの種類です。サポートされているウェーブレットの種類は `WT.haar` と `WT.db` (ダーベシー) です。

# 注意事項

  * 2次元および3次元の変換の場合、ドメインは正方形でなければなりません。言い換えれば、`size(dom,1)==size(dom,2)==size(dom,3)` です。
  * ドメインが長方形の場合は、1D ウェーブレット変換をクロンカー積 (`JopKron`) と組み合わせて使用することを検討してください。
  * ウェーブレット変換は Wavelets.jl パッケージによって提供されています: `http://github.com/JuliaDSP/Wavelets.jl`
  * `Wavelets.jl` によってサポートされている他のウェーブレットクラスを試すことができますが、これらは転置に関して正確性がテストされていません。

# 例

```julia
A = JopDwt(Float64, 64, 64; wt=wavelet(WT.db5))
d = A*rand(domain(A))
```
