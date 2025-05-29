```
SwitchingStencilArray <: AbstractSwitchingStencilArray

SwitchingStencilArray(A::AbstractArray, stencil; 
    boundary=Remove(zero(eltype(parent))),
    padding=Conditional(),
)

`AbstractArray`と[`Stencil`](@ref)、[`BoundaryCondition`](@ref)、[`Padding`](@ref)、および`broadcast_stencil`操作ごとに切り替えられる2つの配列層を持つ。

この操作の使用例は、同じデータに対してステンシル操作が繰り返し実行されるシミュレーションや、フィルター（ぼかしなど）を何度も適用する必要がある場合です。

ほとんどの使用において、`SwitchingStencilArray`は通常の配列とまったく同じように機能します - `dest`配列は安全に無視できます。

ただし、`mapstencil!`を使用する場合は、元の配列ではなく出力を使用する必要があります。切り替えはインプレースではなく、新しい返された配列として行われます。

## 引数

  * `A`: `AbstractArray`
  * `stencil`: [`Stencil`](@ref)。

## キーワード

  * `boundary`: [`Wrap`](@ref)のような[`BoundaryCondition`](@ref)。デフォルトは`Remove()`です。
  * `padding`: [`Conditional`](@ref)や[`Halo{:in}`](@ref)のような[`Padding`](@ref)。デフォルトは`Conditional()`です。

## 例

```

jldoctest using Stencils, Statistics

sa = SwitchingStencilArray(rand(10, 10), Moore(1); boundary=Wrap()) sa .*= 2 # ブロードキャストは通常通り機能します mapstencil(mean, sa) # `mapstencils`を実行するのと同様です s = stencil(sa, 5, 10) # 単一のステンシルを取得します

# しかし、ここで10回の平均ぼかしをインプレースで実行することもできます：

# 注意：`A =`で新しい変数を割り当てないと、配列は

# 切り替わらず、ぼかしも行われません。

let sa = sa     for i in 1:10         sa = mapstencil!(mean, sa)     end end

# 出力

```
