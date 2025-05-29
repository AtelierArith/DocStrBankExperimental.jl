```
default_measure(model)
```

`model`に対して機能する測定値を返すか、信頼できるものが推測できない場合は`nothing`を返します。

Julia 1.9以降では、`nothing`が返されます。これは、StatisticalMeasures.jlがロードされていない限りです。

# 新しい実装

このメソッドは`default_measure(model, observation_scitype)`を呼び出し、フォールバックの戻り値として`nothing`を持ちます。このメソッドのバージョンをオーバーロードすることで`default_measure`を拡張します。例えば、MLJBase.jlパッケージの拡張であるDefaultMeausuresExt.jlを参照してください。
