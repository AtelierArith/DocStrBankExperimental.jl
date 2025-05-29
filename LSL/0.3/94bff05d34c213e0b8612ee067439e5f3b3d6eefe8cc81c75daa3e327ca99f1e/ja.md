```
resolve_bypred(predicate; minimum = 1, timeout = LSL_FOREVER)
```

与えられた述語に一致するすべてのストリームを解決します。

取得したストリームに対してより多くの条件を課すことを可能にする高度なクエリ; 与えられた文字列は<description>ノードのXPath 1.0述語です（周囲の[]は省略）、詳細は http://en.wikipedia.org/w/index.php?title=XPath_1.0&oldid=474981951 を参照してください。

一致するStreamInfoオブジェクトのベクターを返します（descフィールドは空）、これらのいずれかは後でインレットを開くために使用できます。

# 引数:

-`predicate::String`: 述語文字列、例: "name='BioSemi'" または "type='EEG' and                      starts-with(name,'BioSemi') and count(description/desc/channels/channel)=32"

# キーワード引数

-`minimum::Integer`: 少なくともこの数のストリームを返します。 -`timeout::Number`: 操作のタイムアウト、秒単位。タイムアウトが切れると、希望する数のストリーム（おそらくゼロ）が返されます。            
