```
ImplicitFunction
```

*ソルバー*によって定義された暗黙の関数と、解が満たす*条件*のセットのラッパーです。

`ImplicitFunction`オブジェクトは関数のように振る舞い、次のシグネチャを持ちます：

```
y, z = (implicit::ImplicitFunction)(x, args...)
```

最初の出力`y`は最初の引数`x`に関して微分可能であり、2番目の出力`z`（解の副産物）および次の位置引数`args`は定数と見なされます。

導関数が要求されると、条件`c(x, y)`に適用された暗黙の関数定理を使用して`y(x)`のヤコビアンが計算されます（簡潔さのために`z`は無視します）：

```
∂₂c(x, y(x)) * ∂y(x) = -∂₁c(x, y(x))
```

これは、`A * J = -B`という線形システムを解くことを必要とし、ここで`A = ∂₂c`、`B = ∂₁c`、`J = ∂y`です。

# コンストラクタ

```
ImplicitFunction(
    solver,
    conditions,
    linear_solver=KrylovLinearSolver(),
    representation=OperatorRepresentation(),
    backend=nothing,
    preparation=nothing,
    input_example=nothing,
)
```

## 位置引数

  * `solver`: `(x, args...) -> (y, z)`を返す呼び出し可能なオブジェクトで、`z`は解の任意の副産物です。`x`と`y`は両方とも`AbstractArray`のサブタイプでなければならず、`z`と`args`は何でも構いません。
  * `conditions`: 最適性条件のベクトルを返す呼び出し可能なオブジェクトで、`(x, y, z, args...) -> c`の形式で、オートマチック微分と互換性がある必要があります。

## キーワード引数

  * `linear_solver`: 線形システムを解くための呼び出し可能なオブジェクトで、1つは`(A, b)`（単一解）用、もう1つは`(A, B)`（バッチ解）用の2つの必須メソッドを持ちます（デフォルトは[`KrylovLinearSolver`](@ref)）。
  * `representation`: [`MatrixRepresentation`](@ref)または[`OperatorRepresentation`](@ref)のいずれか。
  * `backend::AbstractADType`: `nothing`または[ADTypes.jl](https://github.com/SciML/ADTypes.jl)からのオブジェクトで、条件がどのように微分されるかを指示します。
  * `preparation`: `nothing`または[ADTypes.jl](https://github.com/SciML/ADTypes.jl)からのモードオブジェクト：`ADTypes.ForwardMode()`、`ADTypes.ReverseMode()`または`ADTypes.ForwardOrReverseMode()`のいずれか。
  * `input_example`: `nothing`または微分の準備に使用されるタプル`(x, args...)`のいずれか。
