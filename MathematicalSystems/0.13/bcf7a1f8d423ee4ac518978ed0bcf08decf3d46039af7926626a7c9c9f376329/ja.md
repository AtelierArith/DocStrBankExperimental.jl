```
nextinput(input::VaryingInput, n::Int=1)
```

この入力の最初の `n` 要素を返します。

### 入力

  * `input` – 変動入力
  * `n`     – （オプション、デフォルト: `1`）希望する要素の数

### 出力

この入力の最初の `n` 要素を表す `Base.Iterators.Take` 型のイテレータ。
