```
    getUTCTime(d::CDDate) -> CDDate
```

タイムゾーン情報を削除し、UTCのCDDateを返します。

# 例

```
julia> getUTCTime(CDDate("D:20190425173659+05'30"))
D:20190425120659Z
```
