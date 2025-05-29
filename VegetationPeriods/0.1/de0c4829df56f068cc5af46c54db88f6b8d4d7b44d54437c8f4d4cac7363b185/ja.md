```
Menzel(species; est_prev::Int = 0)
```

開始メソッド `Menzel` は、Menzel (1997) で説明されたアルゴリズムを実装しています。このメソッドは、10種類の一般的な樹木種に対してパラメータ化されています。前年のチルデーが必要です。

引数 `species` は必須で、次のいずれかでなければなりません。

  * `"Larix decidua"`,
  * `"Picea abies (frueh)"`,
  * `"Picea abies (spaet)"`,
  * `"Picea abies (noerdl.)"`,
  * `"Picea omorika"`,
  * `"Pinus sylvestris"`,
  * `"Betula pubescens"`,
  * `"Quercus robur"`,
  * `"Quercus petraea"`,
  * `"Fagus sylvatica"`。

オプションの引数 `est_prev` は、最初の年の前年のチルデーを**推定**するための整数値です。`Menzel` は前年の11月と12月のチルデーの数を必要とします。`est_prev = 0` の場合、時系列の最初の年が前年として使用され、時系列から削除されます。最初の年を保持するために、引数 `est_prev = n` を設定すると、前年のチルデーは最初の `n` 年の平均として推定できます。

## 参考文献

Menzel, A. (1997) Phänologie von Waldbäumen unter sich ändernden Klimabedingungen - Auswertung der Beobachtungen in den Internationalen Phänologischen Gärten und Möglichkeiten der Modellierung von Phänodaten. *Forstliche Forschungsberichte München*。
