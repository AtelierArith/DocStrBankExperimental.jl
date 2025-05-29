```
Broadcasting(f)
```

関数 `f` の「ブロードキャスト」バージョンを表すマッピングを返します。

# 例

```jldoctest
using Gridap.Arrays

a = [3,2]
b = [2,1]

bm = Broadcasting(+)

c = evaluate(bm,a,b)

println(c)

# 出力
[5, 3]
```
