```
kernel(A::MatElem; side::Symbol = :left)
kernel(C::SolveCtx; side::Symbol = :left)
```

行列 $K$ を返します。$K$ の行は $A$ の左カーネルを生成します。すなわち、$KA$ はゼロ行列です。

`side == :right` の場合、$K$ の列は $A$ の右カーネルを生成します。すなわち、$AK$ はゼロ行列です。

基底環が主イデアル整域である場合、$K$ の行または列はそれぞれのカーネルの基底です。

コンテキストオブジェクト `C` が供給される場合、上記は $A = matrix(C)$ に対して適用されます。

#例

```jldoctest
julia> A = QQ[2 6 0 0;1 3 0 0;0 0 5 0];

julia> kernel(A, side=:right)
[-3//1   0//1]
[ 1//1   0//1]
[ 0//1   0//1]
[ 0//1   1//1]

julia> kernel(A)
[-1//2   1//1   0//1]
```
