```
@gapwrap
```

`GAP.Globals`のエントリへのアクセスを含むメソッド定義に適用されると、このマクロはコードを書き換えて、関連するGAPグローバルがキャッシュされ、何度も取得する必要がなくなります。

# 例

```jldoctest
julia> @gapwrap isevenint(x) = GAP.Globals.IsEvenInt(x)::Bool;

julia> isevenint(1)
false

julia> isevenint(2)
true

```
