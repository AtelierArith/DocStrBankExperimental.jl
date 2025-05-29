```
Comic()         # 最新のコミック
Comic(i::Int)   # i 番目の号
```

XKCD APIを介してXKCDコミックのメタデータを取得します: `https://xkcd.com/json.html`.

# 例

```
Comic(552)  # "相関"
```
