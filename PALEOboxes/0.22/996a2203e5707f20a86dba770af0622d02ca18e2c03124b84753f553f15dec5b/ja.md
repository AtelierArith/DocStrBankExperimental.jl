```
VariableReaction(VT, localname => link_namestr, units, description; attributes=Tuple()) -> VariableReaction{VT}
VariableReaction(VT, linklocal_namestr, units, description; attributes=Tuple()) -> VariableReaction{VT}    

VarProp, VarPropScalar, VarPropStateIndep, VarPropScalarStateIndep -> VariableReaction{VT_ReactProperty}
VarDep, VarDepColumn, VarDepScalar, VarDepStateIndep, VarDepColumnStateIndep, VarDepScalarStateIndep -> VariableReaction{VT_ReactDependency}
VarTarget, VarTargetScalar -> VariableReaction{VT_ReactTarget}
VarContrib, VarContribColumn, VarContribScalar -> VariableReaction{VT_ReactContributor}
VarStateExplicit, VarStateExplicitScalar -> VariableReaction{VT_ReactDependency}
VarDeriv, VarDerivScalar -> VariableReaction{VT_ReactContributor}
VarState, VarStateScalar -> VariableReaction{VT_ReactDependency}
VarConstraint, VarConstraintScalar -> VariableReaction{VT_ReactDependency}

[deprecated] VariableReaction(VT, localname, units, description; link_namestr, attributes=Tuple()) -> VariableReaction{VT}
```

モデル変数に対する反応ビュー。

反応は、[`ReactionMethod`](@ref)を作成する際に`VariableReaction`の[`AbstractVarList`](@ref)を定義します。`ReactionMethod`内では、`VariableReaction`は`localname`で参照されます。モデルが初期化されると、同じ`link_namestr`を持つ`VariableReaction`をリンクする[`VariableDomain`](@ref)変数が作成され、データ配列が割り当てられます。次に、`VariableDomain`データ配列の`views`が各タイムステップで[`ReactionMethod`](@ref)関数に渡されます。

# サブタイプ

型パラメータ`VT`は、`VT_ReactProperty`、`VT_ReactDependency`、`VT_ReactContributor`、`VT_ReactTarget`のいずれかであり、便利のために短い名前が定義されています：

```
const VarPropT        = VariableReaction{VT_ReactProperty}
const VarDepT         = VariableReaction{VT_ReactDependency}
const VarTargetT      = VariableReaction{VT_ReactTarget}
const VarContribT     = VariableReaction{VT_ReactContributor}
```

`VariableReaction`と[`VariableDomain`](@ref)のペアリングは2つあります：

  * 反応プロパティと依存変数は、[`VariableDomPropDep`](@ref)にリンクされています。これらは、1つの反応で計算された量を他の反応で使用するために表現するために使用されます。
  * 反応ターゲットと寄与変数は、[`VariableDomContribTarget`](@ref)にリンクされています。これらは、1つの反応がターゲットを定義し、複数の反応が寄与を追加するフラックスのような量を表現するために使用されます。

# 変数属性とコンストラクタの便利関数

変数属性は、変数`:space` [`AbstractSpace`](@ref)（スカラー、セルごとなど）とデータコンテンツ`:field_data` [`AbstractData`](@ref）を定義し、数値ソルバーによって使用される状態変数にラベルを付けるために使用されます。

`VariableReaction`は通常直接呼び出されず、代わりに`VT`と`attributes`の一般的に使用される組み合わせを提供する便利関数が定義されています：

|                      短い名前 |                    VT |    attributes |                 |                    |                       |             |                |
| -------------------------:| ---------------------:| -------------:| ---------------:| ------------------:| ---------------------:| -----------:| --------------:|
|                           |                       |      `:space` |   `:field_data` |       `:vfunction` | `:initialize_to_zero` | `:datatype` | `:is_constant` |
|                           |                       |               |                 |                    |                       |             |                |
|                 `VarProp` |    `VT_ReactProperty` |   `CellSpace` |    `ScalarData` |     `VF_Undefined` |                     - |           - |          false |
|           `VarPropScalar` |    `VT_ReactProperty` | `ScalarSpace` |    `ScalarData` |     `VF_Undefined` |                     - |           - |          false |
|       `VarPropStateIndep` |    `VT_ReactProperty` |   `CellSpace` |    `ScalarData` |     `VF_Undefined` |                     - |   `Float64` |           true |
| `VarPropScalarStateIndep` |    `VT_ReactProperty` | `ScalarSpace` |    `ScalarData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|                           |                       |               |                 |                    |                       |             |                |
|                  `VarDep` |  `VT_ReactDependency` |   `CellSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|            `VarDepColumn` |  `VT_ReactDependency` | `ColumnSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|            `VarDepScalar` |  `VT_ReactDependency` | `ScalarSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|        `VarDepStateIndep` |  `VT_ReactDependency` |   `CellSpace` | `UndefinedData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|  `VarDepColumnStateIndep` |  `VT_ReactDependency` | `ColumnSpace` | `UndefinedData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|  `VarDepScalarStateIndep` |  `VT_ReactDependency` | `ScalarSpace` | `UndefinedData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|                           |                       |               |                 |                    |                       |             |                |
|               `VarTarget` |      `VT_ReactTarget` |   `CellSpace` |    `ScalarData` |     `VF_Undefined` |                `true` |           - |          false |
|         `VarTargetScalar` |      `VT_ReactTarget` | `ScalarSpace` |    `ScalarData` |     `VF_Undefined` |                `true` |           - |          false |
|                           |                       |               |                 |                    |                       |             |                |
|              `VarContrib` | `VT_ReactContributor` |   `CellSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|        `VarContribColumn` | `VT_ReactContributor` | `ColumnSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|        `VarContribScalar` | `VT_ReactContributor` | `ScalarSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|                           |                       |               |                 |                    |                       |             |                |
|        `VarStateExplicit` |  `VT_ReactDependency` |   `CellSpace` |    `ScalarData` | `VF_StateExplicit` |                     - |           - |          false |
|  `VarStateExplicitScalar` |  `VT_ReactDependency` | `ScalarSpace` |    `ScalarData` | `VF_StateExplicit` |                     - |           - |          false |
|                `VarDeriv` | `VT_ReactContributor` |   `CellSpace` |    `ScalarData` |         `VF_Deriv` |                `true` |           - |          false |
|          `VarDerivScalar` | `VT_ReactContributor` | `ScalarSpace` |    `ScalarData` |         `VF_Deriv` |                `true` |           - |          false |
|                           |                       |               |                 |                    |                       |             |                |
|                `VarState` |  `VT_ReactDependency` |   `CellSpace` |    `ScalarData` |         `VF_State` |                     - |           - |          false |
|          `VarStateScalar` |  `VT_ReactDependency` | `ScalarSpace` |    `ScalarData` |         `VF_State` |                     - |           - |          false |
|           `VarConstraint` | `VT_ReactContributor` |   `CellSpace` |    `ScalarData` |    `VF_Constraint` |                `true` |           - |          false |
|     `VarConstraintScalar` | `VT_ReactContributor` | `ScalarSpace` |    `ScalarData` |    `VF_Constraint` |                `true` |           - |          false |

これは、属性の使用に関する一般的な原則を示しています：

  * すべての変数は、`Domain`スカラー、セルごとの量などを指定するために、`:space`変数属性（[`AbstractSpace`](@ref）のサブタイプ）を定義する必要があります。これは配列の次元を定義し、変数がリンクされるときに次元が一致することを確認するために使用されます。
  * `:field_data`属性（[`AbstractData`](@ref）のサブタイプ）は、プロパティおよびターゲット変数が表す量を指定します。これはデフォルトでスカラー値を表す`ScalarData`に設定されます。例えば、単一の同位体を表すには、`:field_data`属性を`IsotopeLinear`に設定する必要があります。`field_data = UndefinedData`の依存変数および寄与変数は、リンクされるときにこの値を取得するか、許可されるリンクを制約するために`:field_data`を指定することができます。
  * `:initialize_to_zero`属性はターゲット変数に設定され、これは（[`add_method_initialize_zero_vars_default!`](@ref)によって作成されたReactionMethodによって）各タイムステップの開始時にゼロに初期化されるべき変数を特定するために使用されます。
  * `:vfunction`属性は、数値ソルバーによってアクセスされる状態変数および対応する時間導関数にラベルを付けるために使用されます。

      * 状態変数と時間導関数のODEのような組み合わせは、ペアの`VarStateExplicit`と`VarDeriv`によって定義されます。これらは単に`:vfunction`属性が設定された`VarDep`と`VarContrib`であり、モデル内に`VarProp`と`VarTarget`は定義されていないことに注意してください（これらは実質的に数値ソルバーによって提供されます）。ペアリングは`varname`と`varname_sms`の命名規則によって定義されます。
      * DAEの代数的制約は、`VarState`と`VarConstraint`によって定義されます。これらは単に`:vfunction`属性が設定された`VarDep`と`VarContrib`であり、モデル内に`VarProp`と`VarTarget`は定義されていないことに注意してください（これらは実質的に数値ソルバーによって提供されます）。これらの変数はペアではありません。
      * `:initialize*to*zero`属性は、寄与変数`VarDeriv`と`VarConstraint`にも設定されます（モデル内に対応するターゲット変数がないため）。
      * `:field_data`属性は、ラベル付き状態変数などに設定する必要があります（モデル内にこれを定義する対応するプロパティまたはターゲット変数がないため）。
  * `:is_constant`属性は、初期化後に変更されない定数プロパティ変数を特定するために使用されます。`:is_constant = true`の依存変数は、定数プロパティ変数にのみリンクできます。
  * `:datatype`属性は、定数変数の具体的なデータ型を提供するためと、非定数変数を自動微分から除外するために使用されます（TODOその使用法を文書化する）。

追加の属性は、モデル固有の情報を提供するために指定でき、デフォルトはReaction .jlコードで定義され、しばしば.yaml構成ファイルで上書きされることができます。[`StandardAttributes`](@ref)を参照してください。例には以下が含まれます：

  * 状態変数または定数変数のための`:initial_value`、`:norm_value`、`:initial_delta`。注：これらの変数を作成する反応は、属性を読み取り、モデル初期化時に変数データ配列を適切に設定するためのセットアップメソッドを実装する責任があります。
  * トレーサー変数にラベルを付けるために使用される`:advect`属性は、モデルに含まれる輸送反応によって適用されるべき輸送を示します。

注：変数がドメイン変数にリンクされた後、使用される属性は`master`変数（プロパティまたはターゲット変数、または対応するプロパティまたはターゲットがないラベル付き状態変数の依存または寄与）からのものです。したがって、追加の属性はこのマスタ変数に設定する必要があります。

# リンクの指定

`localname`は`Reaction`内の`VariableReaction`を特定し、.yaml構成ファイル内で`variable_attributes:`および`variable_links:`を設定するために使用できます。

`linkreq_domain.linkreq_subdomain.linkreq_name`は、[`VariableDomain`](@ref)変数へのランタイムリンクのためのドメイン、サブドメイン、および名前を定義します。

# 引数

  * `VT::VariableType`:  `VT_ReactProperty`、`VT_ReactDependency`、`VT_ReactContributor`、`VT_ReactTarget`のいずれか
  * `localname::AbstractString`: 反応ローカル変数名
  * `link_namestr::AbstractString`: `<linkreq_domain>.[linkreq_subdomain.]linkreq_name`。[`parse_variablereaction_namestr`](@ref)によって解析され、`Domain`変数へのリンクを定義します。
  * `linklocal_namestr::AbstractString`:  `<linkreq_domain>.[linkreq_subdomain.]localname`。ローカル名とドメイン変数へのリンクを定義するための便利な形式で、`linkreq_name == localname`の一般的なケースに対応します。
  * `units::AbstractString`: 単位（該当しない場合は""）
  * `description::AbstractString`: 変数を説明するテキスト

# キーワード

  * `attributes::Tuple(:attrb1name=>attrb1value, :attrb2name=>attrb2value, ...)`: 変数属性、[`StandardAttributes`](@ref)、[`set_attribute!`](@ref)、[`get_attribute`](@ref)を参照してください。
