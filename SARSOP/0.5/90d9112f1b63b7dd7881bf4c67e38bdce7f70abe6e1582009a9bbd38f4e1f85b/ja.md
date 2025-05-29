```
POMDPFile
```

POMDPs.jlの明示的インターフェースを使用して定義されたpomdpからpomdpxファイルを書き込みます。

# コンストラクタ

  * `POMDPFile(filename)` は、ファイルが存在する場合にファイル名を単に保存します
  * `POMDPFile(pomdp::POMDP, filename="model.pomdpx"; verbose=true)` は、pomdp定義から.pomdpxファイルを書き込みます
