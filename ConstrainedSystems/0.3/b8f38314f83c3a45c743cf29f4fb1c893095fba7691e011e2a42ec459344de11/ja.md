```
SaddleSystem
```

構成要素オペレーターブロックから鞍点システムオペレーターを構築します。結果として得られるオブジェクトは、`*` および `\` を使用して乗算および解決に使用できます。鞍点問題は次の形式を持ちます。

$$
\begin{bmatrix}A & B_1^T \\ B_2 & C \end{bmatrix} \begin{pmatrix} u \\ f \end{pmatrix} = \begin{pmatrix} r_1 \\ r_2 \end{pmatrix}
$$

### コンストラクタ

`SaddleSystem(A::AbstractMatrix,B₂::AbstractMatrix,B₁ᵀ::AbstractMatrix,C::AbstractMatrix[,eltype=Float64])`。ブロックは行列として与えられます。適切にスタックするために、一貫したサイズを持っている必要があります。`SaddleSystem(A,B₂,B₁ᵀ)` と呼び出すと、`C` は自動的にゼロに設定されます。

`SaddleSystem(A,B₂,B₁ᵀ,C,u,f[,eltype=Float64])`。オペレーター `A`、`B₂`、`B₁ᵀ`、`C` は、行列、関数、および関数のようなオブジェクトを含むさまざまな形式で与えられます。`u` と `f` は、対応する解と右辺ベクトルのデータ型の例です。ガイドライン：

  * エントリ `A` と `B₂` は `u` に作用できる必要があります（乗算または関数として）。`B₁ᵀ` と `C` は `f` に作用できる必要があります（同様に、乗算または関数として）。
  * `A` と `B₁ᵀ` は `u` 型のデータを返し、`B₂` と `C` は `f` 型のデータを返す必要があります。
  * `A` は可逆であり、演算子 ``and`ldiv!` を装備している必要があります。
  * `u` と `f` は両方とも `AbstractArray` のサブタイプでなければなりません：それらは `size` および `vec` 関数を装備し、`T(data)` という形式のコンストラクタを持っている必要があります。ここで `T` は `u` または `f` のデータ型であり、`data` はラップされたデータ配列です。

`SaddleSystem(A,B₂,B₁ᵀ,u,f)` として呼び出すと、`C` ブロックは省略され、ゼロであると仮定されます。

`SaddleSystem(A,u)` として呼び出すと、これは `SaddleSystem(A,nothing,nothing,u,[])` を呼び出すのと同等であり、これによりオペレーター `A` によって記述された制約のないシステムに戻ります。

これらのコンストラクタのいずれかでのベクトル `u` と `f` のリストは、[`SaddleVector`](@ref) としてまとめることができます。例：`SaddleSystem(A,B₂,B₁ᵀ,SaddleVector(u,f))`。

オプションのキーワード引数 `solver=` を使用して、シュール補完システムの解のタイプを指定できます。デフォルトでは、これは `Direct` に設定されており、シュール補完行列が形成され、因数分解され、保存されます。これは、`BiCGStabl`、`CG`、`GMRES` などのさまざまな反復ソルバーに変更できます。この場合、[`IterativeSolvers.jl`](https://github.com/JuliaLinearAlgebra/IterativeSolvers.jl) からの反復ソルバーが使用されます。
