```
find!(s::Hex, sigstr::AbstractString, start=nothing)
```

バイナリシグネチャを検索し、オフセットを返すか、何も返さない; s._offsetを見つかったシグネチャの先頭を指すように修正します。
