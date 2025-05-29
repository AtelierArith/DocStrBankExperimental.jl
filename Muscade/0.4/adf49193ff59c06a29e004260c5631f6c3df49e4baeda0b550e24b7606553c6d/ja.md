```
DofCost{Class,Nx,Nu,Na,xinod,xfield,uinod,ufield,ainod,
    afield,Tcost,Tcostargs} <: AbstractElement
```

dofの組み合わせにコストを適用する要素です。  

# コンストラクタへの名前付き引数

  * `xinod::NTuple{Nx,𝕫}=()`       `cost`に入る各X-dofの要素ノード番号。
  * `xfield::NTuple{Nx,Symbol}=()` 各X-dofが`cost`に入るフィールド。
  * `uinod::NTuple{Nu,𝕫}=()`       `cost`に入る各U-dofの要素ノード番号。
  * `ufield::NTuple{Nu,Symbol}=()` 各U-dofが`cost`に入るフィールド。
  * `ainod::NTuple{Na,𝕫}=()`       `cost`に入る各A-dofの要素ノード番号。
  * `afield::NTuple{Na,Symbol}=()` 各A-dofが`cost`に入るフィールド。
  * `class:Symbol`                 A-dofのみにコストを適用する場合は`:A`、それ以外は`:I`（"instant"）。
  * `cost::Function`               `class==:I`の場合、`cost(X,U,A,t,costargs...)→ℝ`                                `class==:A`の場合、`cost(A,costargs...)→ℝ`                                 `X`と`U`はタプル（dofの導関数...）であり、`∂0(X)`,`∂1(X)`,`∂2(X)`                                 は`cost`によって`X`（および`U`）の値と導関数にアクセスするために使用されなければなりません。
  * `costargs::NTuple`

# リクエスト可能な内部変数

  * `cost`、コストの値。

# 例

```
ele1 = addelement!(model,DofCost,[nod1],xinod=(1,),field=(:tx1,),
       class=:I,cost=(X,U,A,t)->X[1]^2
```

参照: [`SingleDofCost`](@ref), [`ElementCost`](@ref), [`addelement!`](@ref)  
