```
(success, AST, equationInfo) = getSortedAndSolvedAST(
                                    G, BLT, assign, A, B, stateSelectionFunctions;
                                    log = false, logDetails=false, modelName = "???",
                                    defaultParameterAndStartValues = nothing,
                                    unitless=false)
```

最高導関数レベルのBLT `(G, BLT, assign, A, B)` から、コールバック関数のセット `stateSelectionFunctions` を使用して、この関数はソートされ解決された方程式のAST（抽象構文木）を `Expr` のベクターとして返し、ODE方程式に関する情報（特にODE状態の名前）を提供します。

# 入力引数

  * `G`: G[i] は方程式 i の変数インデックスの整数ベクターです。変数 i はスカラーまたは配列である可能性があります。型は Vector{ Vector{Int} } または Vector{ Any } です。
  * `BLT::Vector{Vector{Int}}`: BLT[i] は BLTブロック i に属する方程式のベクターです。原則として、**BLT[i] には最高導関数方程式のみが含まれている必要があります**。BLT[i] の生成を容易にするために、BLTを計算する関数を呼び出す際にインデックスを前後にマッピングする必要がないように、次の仮定がなされます: もし BLT[j] が **B[j][1] > 0 の方程式を1つだけ含む** なら、このBLTブロックは低次導関数（ダミー）ブロックであり、無視されます。
  * `assign::Vector{Int}`: ei = assign[vi] は変数 vi に割り当てられた方程式 ei です。
  * `A`: パンテリデスアルゴリズムの A-ベクター:      `A[i] = if der(v[i]) == v[k] then k else 0`      ここで `v[i]` は変数 `i` です。
  * `B`: パンテリデスアルゴリズムの B-ベクター:      `B[i] = if der(e[i]) == e[k] then k else 0`      ここで `e[i]` は方程式 `i` です。
  * `stateSelectionFunctions`: `getSortedAndSolvedAST` に必要なコールバック関数に関する情報を保持する不変構造体 [`StateSelectionFunctions`](@ref) のインスタンスです。
  * `log`: = true: デバッグ情報を印刷します（コードのバグを見つけるため）。
  * `logDetails`: = true: `log = true` の場合、詳細なデバッグ情報を印刷します。
  * `modelName`: メッセージで使用されるモデルの名前（それ以外では使用されません）。

# 出力引数

次の値を持つタプル:

  * `success::Bool`: 生成が成功した場合は true、エラーが発生した場合は false。引数 `AST, equationInfo` はエラーが検出されるまでに収集された情報を保持します。
  * `AST::Vector{Expr}`: ソートされ解決された方程式のAST（抽象構文木）を `Expr` のベクターとして表します。
  * `equationInfo::`[`Modia.EquationInfo`](@ref): ODEの状態を定義するオブジェクトです。

変数 `v` に `start` または `init` 属性が定義されていない場合、`start=0.0` があると見なされます。

| 定義済み    | 説明                   |
|:------- |:-------------------- |
| `start` | `start` は初期化中に変更可能です |
| `init`  | `init` は初期化中に変更できません |

注意、`start, init` は状態選択に影響を与えます。

ODE状態に `start` または `init` 値が定義されていない場合、警告メッセージが印刷されます（start/init 値が欠落しています）。

解決された変数に `init` 値がある場合、`log=true` の場合に情報メッセージが印刷されます（init 値は効果がありません）。

# アルゴリズムの概要

注意、*error xxx* という文は、方程式をODEに変換することができないためエラーが発生することを意味します。

## 方程式セットの生成

BLTブロックから、さらなる微分が行われない（= 最高次BLTブロック）方程式セットを生成します。これは [Mattsson and Söderlind (1992)](https://ieeexplore.ieee.org/document/274429) のダミー導関数法によって説明されています。論文 [Otter and Elmqvist (2017)](https://modelica.org/events/modelica2017/proceedings/html/submissions/ecp17132565_OtterElmqvist.pdf) のセクション4.5および4.6も参照してください。

## 初期ODE状態の定義

最初に、すべての微分変数はODE状態として定義されます。アルゴリズムの過程で初期ODE状態が明示的に解決されると、その変数はもはやODE状態ではなくなります。

## 方程式セットの分析

すべての微分レベルのすべての方程式セットに対して、次のアクションを実行します:

  * 方程式セットが *1つの* 方程式と *1つの* 未知数から構成されている場合、その未知数について方程式が解決されます（*不可能な場合はエラー*）。
  * 方程式セットが *N 線形* 方程式と *N* 未知数から構成されている場合、この方程式系を解決します（*線形系でない場合はエラー*）: 方程式は最初に引き裂かれ、反復変数の数を減らし、その後、特別なイテレータループを使用して引き裂かれた方程式系が解決されます。このループは、列ピボッティングを伴うLU分解を使用して線形方程式系を解決します（詳細は [`Modia.LinearEquationsIteration!`](@ref) を参照）。
  * 方程式セットが *N 線形* 方程式と *M* 未知数（*M > N*）から構成されている場合、次のアクションを実行します（*線形系でない場合はエラー*）。 注意、BLTの構造により、この方程式セットは最高導関数レベルに存在することはできません。パンテリデスアルゴリズムにより、M < N は不可能です。

    1. N 未知数について明示的に方程式系を引き裂いて解決します（*不可能な場合はエラー*）。M 未知数の start/init 属性を使用して引き裂きに影響を与えます（例: start または init 値がない変数を最初に排除しようとします）。
    2. N 個の解決された変数は最初はODE状態であり、現在はODE状態ではないと定義されます（いわゆるダミー状態、すなわち代数変数です）。

**すべての方程式** のBLT変換は、選択されたODE状態が知られているという仮定の下で行われます。このフェーズは、最初のダミー導関数の順序付けが必ずしも正しい順序を提供するわけではないため、必要です。このフェーズでは、前のフェーズからの情報が使用されます（すなわち、方程式系のためにすでに決定された引き裂き変数が利用されます）。
