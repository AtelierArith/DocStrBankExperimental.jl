```
drawpath(cp::Path; action=:none, startnewpath=true)
drawpath(cp::Path, action; startnewpath=true)
```

`cp`に格納されたLuxorパスを作成し、`action`を適用します。

パスを作成するには、`storepath()`関数とともに`move()`、`line()`、`curve()`などのパス構築関数に従ってください。

デフォルトでは、`startnewpath=true`であり、新しいパスを開始し、既存のパスの内容を破棄します。
