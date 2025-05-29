```
ContinuousEncoder
```

連続エンコーダを構築するためのモデルタイプで、[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
ContinuousEncoder = @load ContinuousEncoder pkg=MLJModels
```

`model = ContinuousEncoder()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`ContinuousEncoder(drop_last=...)`のようにキーワード引数を提供します。

このモデルを使用して、テーブルのすべての特徴（列）を`Continuous`要素のscitypeを持つように配置します。各特徴`ftr`に対して次のプロトコルを適用します：

  * `ftr`がすでに`Continuous`であれば、そのまま保持します。
  * `ftr`が`Multiclass`であれば、ワンホットエンコードします。
  * `ftr`が`OrderedFactor`であれば、`coerce(ftr, Continuous)`（浮動小数点整数のベクトル）に置き換えます。ただし、`ordered_factors=false`が指定されている場合は、ワンホットエンコードします。
  * `ftr`が`Count`であれば、`coerce(ftr, Continuous)`に置き換えます。
  * `ftr`が他の要素のscitypeを持っている場合、またはエンコーダのフィッティング時に観測されなかった場合は、テーブルから削除します。

**警告：** このトランスフォーマーは、`Multiclass`または`OrderedFactor`列`col`の`levels(col)`がトレーニングデータと変換される新しいデータで同じであることを前提としています。

カテゴリカル特徴を選択的にワンホットエンコードするには（列を削除せずに）、[`OneHotEncoder`](@ref)を代わりに使用してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで

  * `X`: Tables.jl互換の任意のテーブル。列は混合型であっても構いませんが、要素のscitypeが`Multiclass`または`OrderedFactor`のものだけがエンコードされます。列のscitypeは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `drop_last=true`: ワンホットエンコードされた特徴の最終クラスに対応する列を削除するかどうか。例えば、三クラスの特徴は`drop_last=false`の場合に三つの新しい特徴に分割されますが、そうでない場合は二つの特徴になります。
  * `one_hot_ordered_factors=false`: `OrderedFactor`要素のscitypeを持つ特徴をワンホットエンコードするか、または順序を使用して直接（単一の）`Continuous`特徴に強制するかどうか。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次の通りです：

  * `features_to_keep`: テーブルから削除されない特徴の名前
  * `one_hot_encoder`: ワンホットエンコーディングを処理するための`OneHotEncoder`モデルインスタンス
  * `one_hot_encoder_fitresult`: `OneHotEncoder`モデルのフィッティングされたパラメータ

# レポート

  * `features_to_keep`: テーブルから削除されない入力特徴の名前
  * `new_features`: すべての出力特徴の名前

# 例

```julia
X = (name=categorical(["Danesh", "Lee", "Mary", "John"]),
     grade=categorical(["A", "B", "A", "C"], ordered=true),
     height=[1.85, 1.67, 1.5, 1.67],
     n_devices=[3, 2, 4, 3],
     comments=["the force", "be", "with you", "too"])

julia> schema(X)
┌───────────┬──────────────────┐
│ names     │ scitypes         │
├───────────┼──────────────────┤
│ name      │ Multiclass{4}    │
│ grade     │ OrderedFactor{3} │
│ height    │ Continuous       │
│ n_devices │ Count            │
│ comments  │ Textual          │
└───────────┴──────────────────┘

encoder = ContinuousEncoder(drop_last=true)
mach = fit!(machine(encoder, X))
W = transform(mach, X)

julia> schema(W)
┌──────────────┬────────────┐
│ names        │ scitypes   │
├──────────────┼────────────┤
│ name__Danesh │ Continuous │
│ name__John   │ Continuous │
│ name__Lee    │ Continuous │
│ grade        │ Continuous │
│ height       │ Continuous │
│ n_devices    │ Continuous │
└──────────────┴────────────┘

julia> setdiff(schema(X).names, report(mach).features_to_keep) # dropped features
1-element Vector{Symbol}:
 :comments

```

他の情報は[`OneHotEncoder`](@ref)を参照してください。
