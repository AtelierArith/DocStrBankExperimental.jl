```
asofjoin(left::NDSparse, right::NDSparse)
```

`left`の行を`right`の「最も最近の」値と結合します。

# 例

```
using Dates
akey1 = ["A", "A", "B", "B"]
akey2 = [Date(2017,11,11), Date(2017,11,12), Date(2017,11,11), Date(2017,11,12)]
avals = collect(1:4)

bkey1 = ["A", "A", "B", "B"]
bkey2 = [Date(2017,11,12), Date(2017,11,13), Date(2017,11,10), Date(2017,11,13)]
bvals = collect(5:8)

a = ndsparse((akey1, akey2), avals)
b = ndsparse((bkey1, bkey2), bvals)

asofjoin(a, b)
```
