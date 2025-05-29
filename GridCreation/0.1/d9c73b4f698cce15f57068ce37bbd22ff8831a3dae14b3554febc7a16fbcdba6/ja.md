```
mkCartVecs(dx, size[, center])
```

2Dの「グリッド」を作成し、行ベクトルxと列ベクトルyを返します。

グリッドはサンプル間隔dxを持ち、size[0] == size(x)およびsize[1] == size(y)となります。

sizeが整数の場合、[size,size]にブロードキャストされます。

グリッドは、中心要素がゼロを含むように中心に配置されます。centerの特別な値には-1（デフォルト、FFTのような中心）および-2があり、「インターピクセル」サンプリングでは0がsize/2にあります。それ以外の場合、ゼロはcenter番目の要素にあります。

中心のルールはxとyの間で異ならない場合があります。

# 例

## FFT整列グリッド

ceilで丸められた中心要素がゼロを含むことに注意してください。

```julia-repl
julia> x,y = mkCartVecs(.1, 4); # 暗黙の中心=CFFT
julia> x
1×4 LinearAlgebra.Adjoint{Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 -0.2  -0.1  0.0  0.1
julia> collect(y)
4-element Array{Float64,1}:
 -0.2
 -0.1
  0.0
  0.1
```

## インタサンプル整列グリッド

```julia-repl
x,y=mkCartVecs(.1, 4, center=CInterSample);

julia> x
1×4 LinearAlgebra.Adjoint{Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 -0.15  -0.05  0.05  0.15
```

## インデックス中心グリッド

```
julia> x,y=mkCartVecs(.1, 4, center=1);
julia> x
1×4 LinearAlgebra.Adjoint{Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 1.11022e-17  0.1  0.2  0.3
```
