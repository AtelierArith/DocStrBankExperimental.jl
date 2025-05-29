```
loadsmithsoniandata(; clean=false)
```

スミソニアンマイクロビームスタンダードデータセットに関連する成分データをDataFrameとしてロードします。clean=trueを設定すると、"<0.XXX"が0.0に置き換えられ、"missing"が0.0に置き換えられ、文字列値がFloat64として解析されます。データソースはhttps://naturalhistory.si.edu/research/mineral-sciences/collections-overview/reference-materials/smithsonian-microbeam-standardsです。
