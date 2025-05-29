```
@enum Redundancy UNKNOWN_REDUNDANCY LINEARITY_DETECTED NO_REDUNDANCY
```

H-表現またはV-表現の冗長性。

  * `UNKNOWN_REDUNDANCY`: 未検出の線形性または冗長性があるかどうかは不明です。
  * `LINEARITY_DETECTED`: 未検出の線形性はありません。
  * `NO_REDUNDANCY`: 未検出の線形性も冗長性もありません。

V-表現における*未検出の線形性*は、[`Ray`](@ref)の円錐包に暗黙的に含まれる[`Line`](@ref)です。例えば、`conichull([1, 1], [-1, -1])`は、[`Line`](@ref) `Line([1, 1])`を含むため、未検出の線形性があります。未検出の線形性はあまり明白でない場合もあります。例えば、`conichull([1, 0, -1], [0, 1, 1], [-1, -1, 0])`は、最初の2つの[`Ray`](@ref)の和が`Ray([1, 1, 0])`であるため、[`Line`](@ref) `Line([1, 1, 0])`を含んでいます。

H-表現における*未検出の線形性*は、[`HalfSpace`](@ref)の交差に暗黙的に含まれる[`HyperPlane`](@ref)です。例えば、`HalfSpace([1, 1], 1) ∩ HalfSpace([-1, -1], 1)`は、[`HyperPlane`](@ref) `HyperPlane([1, 1], 1)`を含むため、未検出の線形性があります。未検出の線形性はあまり明白でない場合もあります。例えば、`HalfSpace([1, 0], -1) ∩ HalfSpace([0, 1], 1) ∩ HalfSpace([-1, -1], 0)`は、最初の2つの[`HalfSpace`](@ref)の和が`HalfSpace([1, 1], 0)`であるため、[`HyperPlane`](@ref) `HyperPlane([1, 1], 0)`を含んでいます。
