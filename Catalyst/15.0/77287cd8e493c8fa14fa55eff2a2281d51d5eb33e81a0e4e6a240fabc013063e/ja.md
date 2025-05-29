```julia
struct ReactionSystem{V<:Catalyst.NetworkProperties} <: ModelingToolkit.AbstractTimeDependentSystem
```

化学反応のシステム。

# フィールド

  * `eqs`: システムを定義する方程式（反応および代数/微分）。
  * `rxs`: システムを定義する反応。
  * `iv`: 独立変数（通常は時間）。
  * `sivs`: 空間独立変数
  * `unknowns`: すべての従属（未知）変数、種および非種。独立変数を含んではいけません。
  * `species`: 種を表す従属未知変数
  * `ps`: パラメータ変数。独立変数を含んではいけません。
  * `var_to_name`: シンボルを対応する変数にマッピングします。
  * `observed`: 観測変数の方程式。
  * `name`: システムの名前
  * `systems`: 内部サブシステム
  * `defaults`: 初期条件および/またはパラメータが`ODEProblem`に提供されていない場合に使用するデフォルト値。
  * `connection_type`: システムのタイプ
  * `networkproperties`: API関数によって埋められる`NetworkProperties`オブジェクト。内部 – 公開APIの一部とは見なされません。
  * `combinatoric_ratelaws`: 反応速度法則に組み合わせスケーリングを使用するかどうかを設定します。デフォルトはtrueです。
  * `continuous_events`: continuous_events: イベントをモデル化する`Vector{SymbolicContinuousCallback}`。積分器は、ゼロ交差ごとにステップを保証するためにルート探索を使用します。
  * `discrete_events`: discrete_events: イベントをモデル化する`Vector{SymbolicDiscreteCallback}`。与えられた条件が積分ステップの終わりで真であるときに影響を実行する`SciMLBase.DiscreteCallback`のシンボリックアナログ。
  * `metadata`: システムのメタデータ、下流のパッケージで使用されます。
  * `complete`: complete: モデル`sys`が完全である場合、`sys.x`はもはや名前空間を実行しません。
  * `parent`: 簡略化前の階層的親システムで、MTKがインデックス作成で階層的名前空間を機能させるために必要なようです。

# 例

[`Reaction`](@ref) 定義の例から続けます：

```julia
# 種とパラメータを推測するシンプルなコンストラクタ
@named rs = ReactionSystem(rxs, t)

# 種とパラメータの指定を許可
@named rs = ReactionSystem(rxs, t, [A,B,C,D], k)
```

キーワード引数：

  * `observed::Vector{Equation}`: 観測変数を指定する方程式。
  * `systems::Vector{AbstractSystems}`: サブシステムのベクター。`ReactionSystem`、`ODESystem`、または`NonlinearSystem`であることができます。
  * `name::Symbol`: システムの名前（必ず提供する必要があります、または`@named`を使用する必要があります）。
  * `defaults::Dict`: パラメータをそのデフォルト値に、種をそのデフォルト初期値にマッピングする辞書。
  * `checks = true`: 単位をチェックするかどうかのブール値。
  * `networkproperties = NetworkProperties()`: API関数を介して計算されたネットワークプロパティのキャッシュ。
  * `combinatoric_ratelaws = true`: `convert`への呼び出しや`ReactionSystem`を使用したさまざまな問題タイプの呼び出しで使用される`combinatoric_ratelaws`のデフォルト値を設定します。
  * `balanced_bc_check = true`: 反応に現れるBC種がバランスが取れているかどうかをチェックするかどうかを設定します（すなわち、同じ化学量論で基質と生成物の両方として現れる）。

注意：

  * ReactionSystemsは現在、すべての種が同じ単位を持ち、すべての反応が（種の単位）/（時間の単位）の単位を持つことを要求する基本的な単位チェックを行います。単位チェックは、キーワード引数`checks=false`を渡すことで無効にできます。
