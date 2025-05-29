```
commandplot(pf, u, y, p=parameters(pf); kwargs...)
```

役立つプロットを生成します。カスタマイズオプション（`kwargs...`）については、`?pplot`を参照してください。各タイムステップの後に、ユーザーからのコマンドが要求されます。

  * q: 終了
  * s n: `n` ステップ進む

!!! note
    この関数を使用する前に `using Plots` を呼び出す必要があります。

