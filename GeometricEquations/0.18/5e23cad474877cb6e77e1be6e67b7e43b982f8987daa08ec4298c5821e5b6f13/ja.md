EnsembleProblem: ジオメトリック方程式と複数の初期条件および/またはパラメータのセット、統合のための時間範囲、および時間ステップサイズを格納します。

`EnsembleProblem`は、`GeometricEquation`、統合の時間範囲（通常は開始時間と終了時間の2つの値を持つタプル）、時間ステップ、および次の3つのオプションのいずれかを提供することによって初期化されます。

  * 初期条件のベクトルとパラメータセットのベクトル、両方のベクトルが同じ長さであること
  * 初期条件のベクトルと単一のパラメータセット
  * 単一の初期条件とパラメータセットのベクトル

各初期条件は、各状態変数のフィールドを1つ含む`NamedTuple`です。各パラメータセットは、方程式のパラメータを含む`NamedTuple`または方程式にパラメータがないことを示す`NullParameters`のいずれかです。

異なるコンストラクタは、初期条件用のベクトルとパラメータ用のベクトルの2つを生成し、対応するエントリのペアが1つの問題を定義します。最初のケースでは、対応するコンストラクタは両方のベクトルが同じサイズであるかどうかを確認します。2番目のケースでは、対応するコンストラクタは、各エントリが同じパラメータセットを保持するパラメータベクトルを作成します。3番目のケースでは、対応するコンストラクタは、各エントリが同じ初期条件を保持する初期条件ベクトルを作成します。最初と2番目のコンストラクタがメモリの無駄を引き起こすと思われるかもしれませんが、実際にはそれぞれのベクトルは同じ初期条件またはパラメータへの参照のみを保持します。したがって、データは実際には重複していません。

初期条件とパラメータの各ペアはサンプルと呼ばれます。メソッド

```
length(::EnsembleProblem)
nsamples(::EnsembleProblem)
```

は、`EnsembleProblem`内のサンプルの数を返します。単一の初期条件またはパラメータセットは、メソッド

```
initial_condition(::EnsembleProblem, i)
parameter(::EnsembleProblem, i)
```

によって取得できます。ここで、`i`はサンプルのインデックスです。通常、ただし、例えば`GeometricIntegrators`を使用して`EnsembleProblem`のすべてのサンプルを統合する場合、メソッド

```
problem(::EnsembleProblem, i)
```

を介して対応する`GeometricProblem`を取得する方が便利です。

`EnsembleProblem`は、すべてのサンプルを反復処理することも可能です。例えば、

```
for problem in ensemble
    # ...
    # integrate problem
    # ...
end
```

ここで、`ensemble`は`EnsembleProblem`であり、`problem`は対応する`GeometricProblem`です。

### パラメータ

  * `ST <: GeometricEquation`: ディスパッチに使用されるスーパタイプ
  * `DT <: Number`: データ型
  * `TT <: Real`: 時間ステップ型
  * `AT <: AbstractArray{DT}`: 状態変数の配列型
  * `equType <: GeometricEquation`: 方程式型
  * `functionsType <: NamedTuple`: すべての関数メソッドの型
  * `solutionsType <: NamedTuple`: すべての解法メソッドの型
  * `icsType <: AbstractVector{<:NamedTuple}`: すべての初期条件の型
  * `parType <: AbstractVector{<:OptionalParameters}`: パラメータ型

### フィールド

  * `equation`: ベクトルフィールドなどを保持する親方程式オブジェクトへの参照
  * `functions`: 問題を定義するすべてのベクトルフィールドなどのメソッド
  * `solutions`: 定義されている場合、すべての解法などのメソッド
  * `tspan`: 問題の時間範囲 `(t₀,t₁)`
  * `tstep`: シミュレーションで使用される時間ステップ
  * `ics`: 初期条件を含む`NamedTuple`のベクトル、各`NamedTuple`は各状態変数のための1つのフィールドを含む必要があります
  * `parameters`: 方程式のパラメータを含む`NamedTuple`または方程式にパラメータがないことを示す`NullParameters`のベクトル

### コンストラクタ

`EnsembleProblem`は次のコンストラクタを提供します。

```
EnsembleProblem(equ, tspan, tstep, ics::AbstractVector{<:NamedTuple}, parameters::AbstractVector{<:OptionalParameters})
EnsembleProblem(equ, tspan, tstep, ics::AbstractVector{<:NamedTuple}, parameters::OptionalParameters=NullParameters())
EnsembleProblem(equ, tspan, tstep, ics::NamedTuple, parameters::AbstractVector{<:OptionalParameters})
EnsembleProblem(equ, tspan, tstep, ics; parameters = NullParameters()) = 
    EnsembleProblem(equ, tspan, tstep, ics, NullParameters())
EnsembleProblem(equ, tspan, tstep, ics; parameters = NullParameters()) = 
    EnsembleProblem(equ, tspan, tstep, ics, parameters)
```

  * `equ`は`GeometricEquation`のサブタイプです
  * `tspan`は、統合の時間範囲のタプル `(t₀,t₁)` で、`t₀`が開始時間、`t₁`が終了時間です
  * `tstep`は時間ステップで、通常は`AbstractFloat`のサブタイプの値です
  * `ics`は初期条件で、単一のセットまたは複数のセットのベクトルです
  * `parameters`は問題の静的パラメータで、単一のセットまたは複数のセットのベクトルです
