```
select(t::Table, which::Selection)
```

テーブルからすべてまたは一部の列、または単一の列を選択します。

`Selection` は、テーブルから選択できる多くの型の型の和です。次のようになります：

1. `Integer` – この位置の列を返します。
2. `Symbol` – この名前の列を返します。
3. `Pair{Selection => Function}` – 選択を選択し、関数をマッピングし、結果を返します。
4. `AbstractArray` – 配列自体を返します。これはテーブルと同じ長さでなければなりません。
5. `Tuple` of `Selection` – タプル内のすべてのセレクタに対して列を含むテーブルを返します。
6. `Regex` – 正規表現に一致する名前の列を返します。
7. `Type` – 指定された型の要素を持つ列を返します。

# 例：

```
t = table(1:10, randn(10), rand(Bool, 10); names = [:x, :y, :z])

# :x ベクトルを選択
select(t, 1)
select(t, :x)

# :y ベクトルに関数をマッピング
select(t, 2 => abs)
select(t, :y => x -> x > 0 ? x : -x)

# :x と :z のテーブルを選択
select(t, (:x, :z))
select(t, r"(x|z)")

# :x と :y のテーブルに関数をマッピング
select(t, (:x, :y) => row -> row[1] + row[2])
select(t, (1, :y) => row -> row.x + row.y)
```
