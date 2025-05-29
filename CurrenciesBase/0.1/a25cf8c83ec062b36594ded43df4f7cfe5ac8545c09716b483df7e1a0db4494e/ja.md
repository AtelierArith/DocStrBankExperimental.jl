各通貨記号を現在の名前空間にエクスポートします。エクスポートされる個々の単位は、指定された通貨のフルユニットであり、最小単位ではありません。例えば、`@usingcurrencies EUR` は `EUR` をエクスポートし、1€の価値を持つ通貨単位を示します。

```
@usingcurrencies EUR, GBP, AUD
7AUD  # 7.00 AUD
```

`XAU` や `XAG` のような特定の通貨には適切な単位がないため、このマクロはそれらには機能しません。代わりに手動で定義します：

```
const XAU = Monetary(:XAU; precision=4)
```
