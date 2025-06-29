```
@_ func(ex1, [ex2 ...])
```

`ex1,ex2,...` を匿名関数に変換し、`_` プレースホルダーがある場合はそれを `func` に渡します。

詳細なルールは次のとおりです。

1. プレースホルダー `_` の使用は、外側の通常の関数呼び出しに渡される匿名関数の単一引数に展開されます。
2. 番号付きプレースホルダー `_1,_2,...` （または `_₁,_₂,...`）は、引数が複数必要な場合に使用できます。番号は引数リスト内の位置を示します。
3. ダブルアンダースコアプレースホルダー `__` （および番号付きバージョン `__1,__2,...`）は、クロージャスコープを全体の式に拡張します。
4. パイピングおよび合成チェーン `|>,<|,∘` は特別なケースとして扱われ、置換はサブ式に再帰的に入ります。

これらのルールは次の同等性を示唆します。

| 式                         | ルール     | 意味                            |
|:------------------------- |:------- |:----------------------------- |
| `@_ map(_+1, a)`          | (1)     | `map(x->x+1, a)`              |
| `@_ map(_^_, a)`          | (1)     | `map(x->x^x, a)`              |
| `@_ map(_2/_1, a, b)`     | (1,2)   | `map((x,y)->y/x, a, b)`       |
| `@_ func(a,__,b)`         | (3)     | `x->func(a,x,b)`              |
| `@_ func(a,__2,b)`        | (3)     | `(x,y)->func(a,y,b)`          |
| `@_ data \|> map(_.f,__)` | (1,3,4) | `data \|> (d->map(x->x.f,d))` |

# 拡張ヘルプ

## 例

`@_` は、ブロードキャスティング構文が不便な場合の単純なマッピング操作に使用できます。たとえば、コレクション内の各配列の2番目の最後の要素を取得するには：

```jldoctest
julia> @_ map(_[end-1],  [[1,2,3], [4,5]])
2-element Vector{Int64}:
 2
 4
```

引数を複数回繰り返す必要がある場合は、単に `_` を複数回使用します：

```jldoctest
julia> @_ map(_^_,  [1,2,3])
3-element Vector{Int64}:
  1
  4
 27
```

表形式のデータを操作するために、`@_` は便利な構文を提供し、特にダブルアンダースコアプレースホルダー `__` とパイピング構文と組み合わせるときに役立ちます。`__` をテーブル、`_` を個々の行と考えてください：

```jldoctest
julia> table = [(x="a", y=1),
                (x="b", y=2),
                (x="c", y=3)];

julia> @_ table |>
          filter(!startswith(_.x, "a"), __) |>
          map(_.y, __)
2-element Vector{Int64}:
 2
 3
```

## 特殊な関数

ルール1で説明された `_` のスコープは「通常の」関数呼び出しに依存します。これには次の操作が含まれません：

  * 角括弧：`map(_^2,__)[3]` では、匿名関数を受け取るのは `map` であり、これはインデックスが `getindex(...,3)` に低下する前に発生します。内包表記（`collect`）や明示的な行列構築（`hvcat`）も同様に扱われます。
  * ブロードキャスティングおよびフィールドアクセス：`f.(_,xs)` および `f(_,x).y` では、関数 `f` は通常の呼び出しであり、内部の `broadcast` や `getproperty` ではありません。
  * 中置演算子：`sum(_^2,x) / length(x)` は接頭辞形式 `/(...,...)` で書くことができますが、`@_` の慣習はこれを通常の呼び出しと見なさず、したがって匿名関数を `sum` に渡すことです。これは、`map(_^2,x) ./ length(x)` のようなブロードキャストされた演算子にも適用されます。
  * if 文、三項演算子を含む。これはパイプよりも優先度が高いことに注意してください：`data |> (any(_.x<0, __) ? abs.(__) : __) |> step` にはこれらの括弧が必要です。

`__` のスコープはこれらの懸念に影響されません。

| 式                                | 意味                                  |
|:-------------------------------- |:----------------------------------- |
| `@_ data \|> map(_[2],__)[3]`    | `data \|> (d->map(x->x[2],d)[3])`   |
| `@_ [sum(_*_, z) for z in a]`    | `[sum(x->x*x, z) for z in a]`       |
| `@_ sum(1+_^2, data).re`         | `sum(x->1+x^2, data).re`            |
| `@_ sum(_^2,a) / length(a)`      | `sum(x->x^2,a) / length(a)`         |
| `@_ /(sum(_^2,a), length(a))`    | 同じ、接頭辞形式が標準です。                      |
| `@_ data \|> filter(_>3,__).^2`  | `data \|> d->(filter(>(3),d).^2)`   |
| `@_ any(_>3,xs) ? 0 : map(_,ys)` | `any(x->x>3,xs) ? 0 : map(y->y,ys)` |

```
