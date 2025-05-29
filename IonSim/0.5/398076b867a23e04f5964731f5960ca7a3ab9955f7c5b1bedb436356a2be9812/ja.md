```
Chamber(;
        iontrap::LinearChain, B::Real=0, Bhat::NamedTuple{(:x,:y,:z)=ẑ, ∇B::Real=0,
         δB::Union{Real,Function}=0, lasers::Vector{Laser}
)
```

線形チェーン内のイオンの集合がレーザー光と相互作用するためのハミルトニアンを記述するために必要な情報。 **ユーザー定義フィールド**

  * `iontrap<:LinearChain`
  * `B`: Bフィールドの平均的な大きさを表す実数値 [テスラ]。
  * `Bhat::NamedTuple{(:x,:y,:z)}`: Bフィールドの方向を記述します（デフォルトは ẑ）。
  * `∇B`: Bフィールド勾配の大きさ。勾配は常に z方向を指すと仮定します。 [テスラ / メートル]
  * `δB::Function`: Bフィールドの時間依存性 [テスラ]
  * `lasers::Array{<:Laser}`: 配列内の各レーザーについて、指向フィールドには `Tuple{Int,Real}` の配列が含まれるべきです。最初の要素は、レーザーが相互作用する `ions` フィールド内のイオンのインデックスを指定します。2番目の要素は、その相互作用の強さのスケーリングファクターを指定します（例えば、クロストークのモデル化に使用されます）。

**派生フィールド**

  * `_cnst_δB::Bool`: `δB` が定数関数であるかどうかを示すブールフラグ。
  * `basis<:CompositeBasis`: 結合システム（イオン + 振動モード）を記述するための基底。ハミルトニアンを明示的に構築する場合（[`hamiltonian`](@ref)を使用）、基底の順序は慣例として $ion₁ ⊗ ion₂ ⊗ ... ⊗ ion_N ⊗ mode₁ ⊗ mode₂ ⊗ ... ⊗ mode_N$ に設定されます。ここで、イオン基底は `T.iontrap.ions` の順序に従って並べられ、振動モードは `[T.iontrap.selectedmodes.x, T.iontrap.selectedmodes.y, T.iontrap.selectedmodes.z]` の順序に従って並べられます。例えば：

    `chain = LinearChain(ions=[C1, C2], comfrequencies=(x=2e6,y=2e6,z=1e6),   selectedmodes=(x=[1, 2], y=[], z=[1]))`

    基底の順序は次のようになります。

    `C1.basis ⊗ C2.basis ⊗ chain.selectedmodes.x[1].basis   ⊗ chain.selectedmodes.x[2].basis ⊗ chain.selectedmodes.z[1].basis`

    さもなければ、順序はソルバーで使用される初期状態の形式に従います。

```
