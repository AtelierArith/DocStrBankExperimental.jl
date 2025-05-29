```
pay!(buyer::Balance,
    seller::Balance,
    price::Price,
    timestamp::Integer;
    comment::String = "")
```

# 戻り値

価格が全額支払われたかどうかを示すブール値。
