```
Weather(data[, metadata])
```

天候を定義します。すなわち、1つ以上の時間ステップにおける大気の局所的な条件です。各時間ステップは[`Atmosphere`](@ref)構造体を使用して記述され、結果として得られる構造体は`TimeStepTable`です。

`Weather`をインスタンス化する最も簡単な方法は、`DataFrame`を入力として使用することです。

`DataFrame`は、各行が特定の時間ステップの観測値であり、各列が変数であるようにフォーマットされている必要があります。列名は[`Atmosphere`](@ref)構造体の変数名と正確に一致する必要があります。

## 参照

  * [`Atmosphere`](@ref)構造体
  * Archimed形式の気象データを読み込むための[`read_weather`](@ref)関数。

## 例

手動で定義された天候データの例（面倒）：

```julia
w = Weather(
    [
        Atmosphere(T = 20.0, Wind = 1.0, P = 101.3, Rh = 0.65),
        Atmosphere(T = 23.0, Wind = 1.5, P = 101.3, Rh = 0.60),
        Atmosphere(T = 25.0, Wind = 3.0, P = 101.3, Rh = 0.55)
    ],
    (
        site = "テストサイト",
        important_metadata = "これは重要で、私たちの天候データに添付されます"
    )
)
```

`Weather`は`TimeStepTable{Atmosphere}`なので、`DataFrame`に変換できます：

```julia
using DataFrames
df = DataFrame(w)
```

そして再び`Weather`に戻して`TimeStepTable{Atmosphere}`を作成します：

```julia
Weather(df, (site = "私のサイト",))
```

もちろん、`Atmosphere`にリストされている必要な変数が少なくとも含まれている任意の`DataFrame`で機能します。
