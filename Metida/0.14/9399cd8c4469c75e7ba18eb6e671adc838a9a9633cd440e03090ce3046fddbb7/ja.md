```
@lmmformula(formula, args...)
```

分散共分散構造表現を持つ式を作成するためのマクロです。`@lmmformula`は短い`LMM`構築に使用できます。

例:

```
lmm = Metida.LMM(@lmmformula(var~sequence+period+formulation,
random = formulation|subject:CSH,
repeated = formulation|subject:DIAG),
df0)
```

は次のように等しいです:

```
lmm = LMM(@formula(var~sequence+period+formulation), df0;
random = VarEffect(@covstr(formulation|subject), CSH),
repeated = VarEffect(@covstr(formulation|subject), DIAG),
)
```

`@lmmformula`は3つのコンポーネントを持ちます - 1つ目は固定効果のための式で、`StatsModels`のように定義されます（1つ目の引数は単に`@formula`マクロに提供されます）。他の引数はキーワードのように定義する必要があります。`repeated`キーワードは繰り返し効果部分を定義し、`random`はランダム効果部分を定義します。以下の例のように、複数のランダム因子を使用できます:

```
lmm = LMM(@lmmformula(var~sequence+period+formulation,
random = formulation|subject:CSH,
random = 1|subject:DIAG,
repeated = formulation|subject:DIAG),
df0)
```

`random`または`repeated`構造はテンプレートによって作成されます:

`効果式` | `ブロッキング因子` [/ `ネスト因子`] [: `共分散構造`]

`|` - 効果式とブロッキング因子の定義を分けます（必須です）、`/`と`:`の修飾子はオプションです。

`/`はMixedModelsやRegressionFormulaeのように機能し、因子`f|a/b`を`f|a` + `f|a&b`に展開します。繰り返し効果の定義には使用できません。

`:` - 共分散構造は`:`の直後に定義されます（SI、DIAG、CS、CSHなど...）、`:`が使用されない場合はこの効果に対してSIが使用されます。

`a+b`や`a*b`のような用語はブロッキング因子として使用すべきではありません。
