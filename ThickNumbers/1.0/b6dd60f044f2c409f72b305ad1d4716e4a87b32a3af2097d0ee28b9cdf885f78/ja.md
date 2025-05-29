```
mig(x::ThickNumber)
```

`x`の最小絶対値。IEEE Std 1788-2015の表9.2で要求されています。

# デフォルト実装

デフォルトの実装は、集合にゼロが含まれているかどうかを確認し、含まれている場合はゼロを返します。そうでない場合は、端点の最小絶対値を返します：

```
mig(x::ThickNumber) = zero(T) ∈ x ? zero(T) : min(abs(loval(x)), abs(hival(x)))
```
