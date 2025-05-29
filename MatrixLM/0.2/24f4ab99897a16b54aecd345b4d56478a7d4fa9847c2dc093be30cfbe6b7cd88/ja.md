```
design_matrix(frml, df::DataFrame, cntrst::Dict{Symbol, AbstractContrasts})

数式項とデータソースに基づいて設計行列を返します。

# 引数 

- `frml`: マクロ `@mlmformula` によって生成された数式項
- `df`: データソーステーブルを含むデータフレーム
- `cntrst`: カテゴリカルまたは順序変数のエンコーディング方法を説明する辞書、`StatsModels.jl` に基づく
```

---

```
design_matrix(frml, df::DataFrame, cntrst::Vector)

数式項とデータソースに基づいて設計行列を返します。

# 引数 

- `frml`: マクロ `@mlmformula` によって生成された数式項
- `df`: データソーステーブルを含むデータフレーム
- `cntrst`: 変数名と対応するエンコーディング関数のタプルを含むベクター。
```

---

```
design_matrix(frml, df::DataFrame)

数式項とデータソースに基づいてデフォルトの設計行列を返します。この場合、すべてのカテゴリカル変数はダミーコーディングされます。

# 引数 

- `frml`: マクロ `@mlmformula` によって生成された数式項
- `df`: データソーステーブルを含むデータフレーム
```
