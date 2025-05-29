```
@truthtable formula [full=false]
```

命題式（論理式）の真理値表を作成します。

`full`はオプションのキーワード引数で、デフォルトは`false`です。`full`が`true`の場合、真理値表は展開形式で作成されます。

## 論理演算子のリスト

  * AND: `&&`, `&`, `∧` (`\wedge<tab>`)
  * OR: `||`, `|`, `∨` (`\vee<tab>`)
  * NOT: `!`, `~`, `¬` (`\neg<tab>`)
  * XOR: `⊻` (`\xor<tab>`)
  * NAND: `⊼` (`\nand<tab>`)
  * NOR: `⊽` (`\nor<tab>`)
  * IMPLICATION: `-->`, `→` (`\to<tab>` または `\rightarrow<tab>`), `⇒` ( `\Rightarrow<tab>`)
  * EQUIVALENCE: `<-->`, `===`, `≡` (`\equiv<tab>`), `↔` (`\leftrightarrow<tab>`), `⇔` (`\Leftrightarrow<tab>`)

# 例

```julia
julia> @truthtable p || q
TruthTable
┌───────┬───────┬───────┐
│   p   │   q   │ p ∨ q │
├───────┼───────┼───────┤
│ true  │ true  │ true  │
│ true  │ false │ true  │
│ false │ true  │ true  │
│ false │ false │ false │
└───────┴───────┴───────┘

julia> @truthtable p & (~q | r)
TruthTable
┌───────┬───────┬───────┬──────────────┐
│   p   │   q   │   r   │ p ∧ (¬q ∨ r) │
├───────┼───────┼───────┼──────────────┤
│ true  │ true  │ true  │ true         │
│ true  │ true  │ false │ false        │
│ true  │ false │ true  │ true         │
│ true  │ false │ false │ true         │
│ false │ true  │ true  │ false        │
│ false │ true  │ false │ false        │
│ false │ false │ true  │ false        │
│ false │ false │ false │ false        │
└───────┴───────┴───────┴──────────────┘

julia> @truthtable p & (~q | r) full=true
TruthTable
┌───────┬───────┬───────┬───────┬────────┬──────────────┐
│   p   │   q   │   r   │  ¬q   │ ¬q ∨ r │ p ∧ (¬q ∨ r) │
├───────┼───────┼───────┼───────┼────────┼──────────────┤
│ true  │ true  │ true  │ false │ true   │ true         │
│ true  │ true  │ false │ false │ false  │ false        │
│ true  │ false │ true  │ true  │ true   │ true         │
│ true  │ false │ false │ true  │ true   │ true         │
│ false │ true  │ true  │ false │ true   │ false        │
│ false │ true  │ false │ false │ false  │ false        │
│ false │ false │ true  │ true  │ true   │ false        │
│ false │ false │ false │ true  │ true   │ false        │
└───────┴───────┴───────┴───────┴────────┴──────────────┘

julia> @truthtable p ∨ q <--> r full=false
TruthTable
┌───────┬───────┬───────┬──────────────┐
│   p   │   q   │   r   │ p ∨ q <--> r │
├───────┼───────┼───────┼──────────────┤
│ true  │ true  │ true  │ true         │
│ true  │ true  │ false │ false        │
│ true  │ false │ true  │ true         │
│ true  │ false │ false │ false        │
│ false │ true  │ true  │ true         │
│ false │ true  │ false │ false        │
│ false │ false │ true  │ false        │
│ false │ false │ false │ true         │
└───────┴───────┴───────┴──────────────┘

julia> @truthtable p ∨ q <--> r full=true
TruthTable
┌───────┬───────┬───────┬───────┬──────────────┐
│   p   │   q   │   r   │ p ∨ q │ p ∨ q <--> r │
├───────┼───────┼───────┼───────┼──────────────┤
│ true  │ true  │ true  │ true  │ true         │
│ true  │ true  │ false │ true  │ false        │
│ true  │ false │ true  │ true  │ true         │
│ true  │ false │ false │ true  │ false        │
│ false │ true  │ true  │ true  │ true         │
│ false │ true  │ false │ true  │ false        │
│ false │ false │ true  │ false │ false        │
│ false │ false │ false │ false │ true         │
└───────┴───────┴───────┴───────┴──────────────┘
```
