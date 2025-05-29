```
@astable(args...)
```

`@astable`は、DataFramesMeta.jlマクロの`@select`、`@transform`、およびそれらの変更可能および行単位の同等物の内部での単一の変換から`NamedTuple`を返します。

`@astable`は単一のブロックに作用します。すべてのトップレベルの式を通じて動作し、`:y = ...`または`$y = ...`の形式のすべての式を収集します。つまり、`Symbol`への代入またはエスケープされた列識別子への代入であり、これはDataFramesMeta.jlマクロの外では構文エラーです。式の最後に、すべての代入が`NamedTuple`に収集され、DataFrames.jlの変換ミニ言語で`AsTable`の宛先と共に使用されます。

具体的には、次の式が

```
df = DataFrame(a = 1)

@rtransform df @astable begin
    :x = 1
    y = 50
    :z = :x + y + :a
end
```

次のペアになります。

```
function f(a)
    x_t = 1
    y = 50
    z_t = x_t + y + a

    (; x = x_t, z = z_t)
end

transform(df, [:a] => ByRow(f) => AsTable)
```

`@astable`には、複雑さが増す代償として2つの大きな利点があります。第一に、`@astable`は単一の変換から複数の列を簡単に作成でき、スコープを共有します。たとえば、`@astable`は次のようなことを可能にします（ここで`:x`と`:x_2`はすでにデータフレームに存在します）。

```
@transform df @astable begin
    m = mean(:x)
    :x_demeaned = :x .- m
    :x2_demeaned = :x2 .- m
end
```

`:x_demeaned`と`:x2_demeaned`の作成は両方とも変数`m`を共有し、二度計算する必要はありません。

第二に、`@astable`は中間計算を行い、その結果を新しい列に保存する際に便利です。たとえば、次のようなコードは失敗します。

```
@rtransform df begin
    :new_col_1 = :x + :y
    :new_col_2 = :new_col_1 + :z
end
```

これは、DataFrames.jlが変換の逐次評価を保証しないためです。`@astable`はこの問題を解決します。

```
@rtransform df @astable begin
    :new*col*1 = :x + :y
    :new*col*2 = :new*col*1 + :z
end
```

`@astable`における列の代入は、他のDataFramesMeta.jlマクロにおける列の代入と同様のルールに従います。列の代入の左辺は、`Symbol`または`Symbol`または`AbstractString`に評価される任意の式であることができます。たとえば、`:y = ...`および`$y = ...`は新しい列を代入するための有効な方法です。しかし、他のDataFramesMeta.jlマクロとは異なり、`AsTable`を介した複数列の代入は許可されていません。次のようなコードは失敗します。

```
@transform df @astable begin
    DataFrames.AsTable = :x
end
```

既存の列への参照も、他のDataFramesMeta.jlマクロと同じルールに従います。

### 例

```
julia> df = DataFrame(a = [1, 2, 3], b = [4, 5, 6]);

julia> d = @rtransform df @astable begin
           :x = 1
           y = 5
           :z = :x + y
       end
3×4 DataFrame
 Row │ a      b      x      z
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      4      1      6
   2 │     2      5      1      6
   3 │     3      6      1      6

julia> df = DataFrame(a = [1, 1, 2, 2], b = [5, 6, 70, 80]);

julia> @by df :a @astable begin
            ex = extrema(:b)
            :min_b = first(ex)
            :max_b = last(ex)
       end
2×3 DataFrame
 Row │ a      min_b  max_b
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      5      6
   2 │     2     70     80

julia> new_col = "New Column";

julia> @rtransform df @astable begin
           f_a = first(:a)
           $new_col = :a + :b + f_a
           :y = :a * :b
       end
4×4 DataFrame
 Row │ a      b      New Column  y
     │ Int64  Int64  Int64       Int64
─────┼─────────────────────────────────
   1 │     1      5           7      5
   2 │     1      6           8      6
   3 │     2     70          74    140
   4 │     2     80          84    160
```
