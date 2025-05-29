```
Window()
Window(electron_options::Dict; async=true)
```

Electronを通じて新しいウィンドウを作成して開きます。

`async==false`の場合、この関数はウィンドウが完全に初期化され、javascriptまたはBlink APIを介して通信できる準備が整うまでブロックします。

`electron_options`辞書はElectronウィンドウを初期化するために使用されます。Electronオプションの完全なセットについては、こちらを参照してください: https://electronjs.org/docs/api/browser-window#new-browserwindowoptions
