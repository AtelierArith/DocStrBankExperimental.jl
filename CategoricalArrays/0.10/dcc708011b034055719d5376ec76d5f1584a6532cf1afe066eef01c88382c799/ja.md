```
recode!(dest::AbstractArray, src::AbstractArray[, default::Any], pairs::Pair...)
```

`dest`に`src`から要素を埋め込み、`pairs`のキーに一致するものは対応する値で置き換えます。

`pairs`の各`Pair`について、要素がキー（ペアの最初の項目）と等しい場合（`isequal`に従って）や、コレクションである場合はそのエントリのいずれかと等しい場合、対応する値（2番目の項目）が`dest`にコピーされます。要素がキーに一致せず、`default`が指定されていないか`nothing`の場合は、そのままコピーされます。`default`が指定されている場合は、元の要素の代わりに使用されます。`dest`と`src`は同じ長さでなければなりませんが、同じ型である必要はありません。`src`の要素および`pairs`からの値は、可能な限り代入時に`convert`されます。要素が複数のキーに一致する場合、最初の一致が使用されます。

```
recode!(dest::CategoricalArray, src::AbstractArray[, default::Any], pairs::Pair...)
```

`dest`が`CategoricalArray`の場合、結果のレベルの順序は渡された`pairs`の順序によって決定され、`default`が提供されている場合は最後のレベルになります。

```
recode!(dest::AbstractArray, src::AbstractArray{>:Missing}[, default::Any], pairs::Pair...)
```

`src`に欠損値が含まれている場合、それらは決して`default`で置き換えられません：ペアで`missing`を使用して再コーディングします。
