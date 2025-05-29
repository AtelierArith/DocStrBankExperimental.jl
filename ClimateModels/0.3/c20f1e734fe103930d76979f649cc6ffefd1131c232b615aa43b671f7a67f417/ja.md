```
log( x :: AbstractModelConfig, y :: String; fil="", msg="", prm=false)
```

`log`フォルダ（すなわち、`joinpath(x,"log")`）に`git`コミットを表示または追加します。

1. キーワードが提供されていない場合、`y`は`log(x)`からのコミットIDである必要があります。
2. キーワード引数は相互排他的であり（すなわち、一度に1つだけ使用）、次のように機能します：

  * `msg`が空でない`String`の場合：メッセージ`y`で`log/README.md`にコミット`msg`を追加します。
  * `fil`が空でない`String`の場合：メッセージ`y`で`log/$(fil)`の変更をコミットします。`log/$(fil)`がgitに知られていない場合（すなわち、コミットがエラーになる場合）、最初に`log/$(fil)`を追加しようとします。
  * `prm`が`true`の場合：`input`または`tracked_parameters/`に見つかったファイル（あれば）をgitログに追加します。

例：

```
MC=run(ModelConfig(ClimateModels.RandomWalker,(NS=100,)))
MC.inputs[:NS]=200
msg="tracked_parameters.tomlを更新（または最新の場合はスキップ）"
log(MC,msg,prm=true)
log(MC)
```
