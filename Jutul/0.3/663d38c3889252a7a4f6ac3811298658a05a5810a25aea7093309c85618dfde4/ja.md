```
n = number_of_equations_per_entity(model::JutulModel, eq::JutulEquation)
```

エンティティごとの方程式の数を取得します。たとえば、2つの成分の質量収支は、グリッドセル（= エンティティ）ごとに2つの方程式を持ちます。
