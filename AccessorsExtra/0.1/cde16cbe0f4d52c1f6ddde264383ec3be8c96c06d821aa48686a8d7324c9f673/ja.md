```
maybe(optic; [default=nothing])
```

オブジェクト内に存在するかもしれない値を参照するオプショナルオプティックを作成します。

**注意:** `default != nothing` のサポートは実験的であり、取得のためにのみ実装されています。設定には対応していません。

`maybe(o)` は `o` 自体と似た動作をしますが、以下の違いがあります：

  * 参照されている値が存在する場合、`set(obj, maybe(o), nothing)` はそれを削除します
  * 値が存在しない場合：

      * `maybe(o)(obj)` にアクセスすると `default` が返されます
      * `modify` は何もしません
      * `set` は新しい値を挿入します

参照されている値が存在するかどうかは、`hasoptic(obj, o)` によって決定されます。

`@maybe` は便利のために利用可能なマクロ形式です： `@maybe ...` は `maybe(@o ...)` と同等です。

## 例

```julia
julia> o = maybe(@o _.a)

julia> o((a=1, b=2))
1
julia> o((b=2,))
# nothing

julia> set((a=1, b=2), o, 10)
(a = 10, b = 2)
julia> set((b=2,), o, 10)
(b = 2, a = 10)

julia> modify(x -> x+10, (a=1, b=2), o)
(a = 11, b = 2)
julia> modify(x -> x+10, (b=2,), o)
(b = 2,)

julia> modify(x -> x+10, ((a=1,), (a=2, b=3), (b=4,)), o ∘ Elements())
((a = 11,), (a = 12, b = 3), (b = 4,))
```
