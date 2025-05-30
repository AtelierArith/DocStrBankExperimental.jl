```
system(expr...)
```

与えられた式に対応するシステム型のインスタンスを返します。

### 入力

  * `expr` – 動的方程式、制約集合、またはシステムの次元を定義するカンマで区切られた式

### 出力

与えられた式に最も適したシステム。

### 注意事項

**用語。** 式 `expr` には、以下のサブ式の1つ以上が含まれます：

  * 動的方程式、連続的なもの、例えば `x' = Ax`、または離散的なもの、例えば `x⁺ = Ax`
  * 集合制約、例えば `x ∈ X`
  * 入力制約、例えば `u ∈ U`
  * 次元、例えば `dim: (2,1)` または `dim = 1`
  * 入力変数の指定、例えば `input: u` または `input = u`
  * ノイズ変数の指定、例えば `noise: w` または `noise = w`

マクロ呼び出しは、次のように前述のサブ式（以下、*用語*と呼ぶ）を区切って形成されます：

```julia
@system(dynamic eq., set constr., input constr., input specif., noise spec., dimens.)
```

システムの定義を構成する異なる用語は、特定の順序で現れる必要はありません。さらに、必須の用語は動的方程式のみであり、他の用語はオプションであり、システムの種類に応じてデフォルト値が適用される場合があります。これは次に説明します。

**動的方程式。** 連続システムにおける時間微分は、`'` を使用して指定されます。例えば `x' = A*x` のように。離散システムは `⁺` を使用して指定されます（これはキーの組み合わせ `\^+[TAB]` で書くことができます）。例えば `x⁺ = A*x` のように。さらに、行列ベクトル積を示すアスタリスクはオプションです。例えば、`x' = Ax` と `x' = A*x` の両方は、状態行列が `A` である線形連続システムとして解析されます。行列は呼び出しサイトで定義されている必要があります。

**デフォルト値。** 動的方程式が解析されると、左辺の変数は状態変数として解釈されます。入力変数はデフォルトで `u` であり、ノイズ変数はデフォルトで `w` です。入力変数のデフォルト名を変更したい場合は、`input: var`（または同等に `input=var`）という用語を追加することで行うことができます。ここで `var` は入力変数の新しい名前に対応します。例えば `@system(x' = A*x + B*v, input:v)` のように。同様に、ノイズ変数は `noise: var` または `noise=var` で指定されます。

**例外。** 次の例外および特別なケースが適用されます：

  * 右辺が `A*x + B*foo`、`A*x + B*foo + c` または `f(x, foo)` の形をしている場合、方程式は制御線形（アフィン）または制御ブラックボックスシステムとして解析され、入力は `foo` となります。この場合、`input` 変数はデフォルト値の `u` に対応せず、`foo` が入力として解析されます。
  * 左辺に `E*x⁺` または `E*x'` の形の乗法項が含まれている場合、方程式は代数方程式として解析され、したがって記述子システムが生じます。この場合、アスタリスク `*` 演算子は必須です。
  * `x' = α*x` の形のシステムは、`α` がスカラーである場合、線形システムとして解析されます。デフォルトの次元は `1` であり、`α` は `Float64` として解析されます。システムが高次元の場合は、`dim` を使用します。例えば `x' = 2x, dim=3` のように。

### 例

まず、このマクロを使用して連続線形システムを作成しましょう：

```jldoctest system_macro
julia> A = [1. 0; 0 1.];

julia> @system(x' = A*x)
LinearContinuousSystem{Float64, Matrix{Float64}}([1.0 0.0; 0.0 1.0])
```

離散システムは `⁺` を使用して定義されます：

```jldoctest system_macro
julia> @system(x⁺ = A*x)
LinearDiscreteSystem{Float64, Matrix{Float64}}([1.0 0.0; 0.0 1.0])
```

さらに、集合定義 `x ∈ X` を追加して制約のあるシステムを作成できます。例えば、制約された状態と入力を持つ離散制御アフィンシステムは次のように書かれます：

```jldoctest system_macro
julia> using LazySets

julia> B = Matrix([1.0 0.5]');

julia> c = [1.0, 1.5];

julia> X = BallInf(zeros(2), 10.0);

julia> U = BallInf(zeros(1), 2.0);

julia> @system(x' = A*x + B*u + c, x ∈ X, u ∈ U)
ConstrainedAffineControlContinuousSystem{Float64, Matrix{Float64}, Matrix{Float64}, Vector{Float64}, BallInf{Float64, Vector{Float64}}, BallInf{Float64, Vector{Float64}}}([1.0 0.0; 0.0 1.0], [1.0; 0.5;;], [1.0, 1.5], BallInf{Float64, Vector{Float64}}([0.0, 0.0], 10.0), BallInf{Float64, Vector{Float64}}([0.0], 2.0))
```

ブラックボックスシステムを作成するには、状態、入力、ノイズの次元を別々に定義する必要があります。制約された制御ブラックボックスシステムの場合、マクロは次のように書かれます：

```jldoctest system_macro
julia> f(x, u) = x + u;

julia> @system(x⁺ = f(x, u), x ∈ X, u ∈ U, dim: (2,2))
ConstrainedBlackBoxControlDiscreteSystem{typeof(f), BallInf{Float64, Vector{Float64}}, BallInf{Float64, Vector{Float64}}}(f, 2, 2, BallInf{Float64, Vector{Float64}}([0.0, 0.0], 10.0), BallInf{Float64, Vector{Float64}}([0.0], 2.0))
```
