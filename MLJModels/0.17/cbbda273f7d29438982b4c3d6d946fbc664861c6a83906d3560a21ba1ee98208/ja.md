```
OneHotEncoder
```

[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づいて、MLJモデルインターフェースを実装するためのワンホットエンコーダを構築するためのモデルタイプ。

MLJからは、次のようにしてタイプをインポートできます。

```
OneHotEncoder = @load OneHotEncoder pkg=MLJModels
```

`model = OneHotEncoder()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`OneHotEncoder(features=...)`のようにキーワード引数を提供します。

このモデルを使用して、テーブルの`Multiclass`および`OrderedFactor`特徴（列）をワンホットエンコードし、他の列は変更しないでください。

変換される新しいデータには、フィットデータに存在する特徴が欠けている場合がありますが、*新しい*特徴が存在することはできません。

**警告:** このトランスフォーマーは、任意の`Multiclass`または`OrderedFactor`列`col`の`levels(col)`が、トレーニングデータと変換される新しいデータで同じであると仮定します。

*すべての*特徴を`Continuous`特徴に変換するか、削除するには、代わりに[`ContinuousEncoder`](@ref)を使用してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで

  * `X`: 任意のTables.jl互換テーブル。列は混合型であることができますが、`Multiclass`または`OrderedFactor`の要素スカイタイプを持つ列のみがエンコードされます。列のスカイタイプは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `features`: シンボルのベクター（列名）。空の場合（デフォルト）、すべての`Multiclass`および`OrderedFactor`特徴がエンコードされます。それ以外の場合、エンコーディングは指定された特徴（`ignore=false`）または指定されていない特徴（`ignore=true`）にさらに制限されます。このデフォルトの動作は、`ordered_factor`フラグによって変更できます。
  * `ordered_factor=false`: `true`の場合、`OrderedFactor`特徴は普遍的に除外されます。
  * `drop_last=true`: エンコードされた特徴の最終クラスに対応する列を削除するかどうか。たとえば、3クラスの特徴は、`drop_last=false`の場合に3つの新しい特徴に分割されますが、それ以外の場合は2つの特徴のみになります。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `all_features`: トレーニング中に遭遇したすべての特徴の名前
  * `fitted_levels_given_feature`: 各エンコードされた特徴に関連付けられたレベルの辞書。特徴名でキー付けされています。
  * `ref_name_pairs_given_feature`: ペア`r => ftr`（たとえば、`0x00000001 => :grad__A`）の辞書。ここで`r`はレベルを表すCategoricalArrays.jlの参照整数であり、`ftr`は対応する新しい特徴名です。辞書はエンコードされた特徴の名前でキー付けされています。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `features_to_be_encoded`: エンコードされる入力特徴の名前
  * `new_features`: すべての出力特徴の名前

# 例

```
using MLJ

X = (name=categorical(["Danesh", "Lee", "Mary", "John"]),
     grade=categorical(["A", "B", "A", "C"], ordered=true),
     height=[1.85, 1.67, 1.5, 1.67],
     n_devices=[3, 2, 4, 3])

julia> schema(X)
┌───────────┬──────────────────┐
│ names     │ scitypes         │
├───────────┼──────────────────┤
│ name      │ Multiclass{4}    │
│ grade     │ OrderedFactor{3} │
│ height    │ Continuous       │
│ n_devices │ Count            │
└───────────┴──────────────────┘

hot = OneHotEncoder(drop_last=true)
mach = fit!(machine(hot, X))
W = transform(mach, X)

julia> schema(W)
┌──────────────┬────────────┐
│ names        │ scitypes   │
├──────────────┼────────────┤
│ name__Danesh │ Continuous │
│ name__John   │ Continuous │
│ name__Lee    │ Continuous │
│ grade__A     │ Continuous │
│ grade__B     │ Continuous │
│ height       │ Continuous │
│ n_devices    │ Count      │
└──────────────┴────────────┘
```

[`ContinuousEncoder`](@ref)も参照してください。
