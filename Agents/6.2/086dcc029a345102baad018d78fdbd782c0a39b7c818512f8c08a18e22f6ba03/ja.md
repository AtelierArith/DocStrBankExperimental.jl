```
abmexploration(model::ABM; alabels, mlabels, kwargs...)
```

エージェントベースモデルを探索し、パラメータの変更が時間の進化に与える影響を調べるためのインタラクティブなアプリケーションを開きます。`Agents`が必要です。

このアプリケーションは、ABMをインタラクティブに進化させ、その進化をプロットし、モデルのパラメータをインタラクティブに変更できるようにし、収集されたデータの進化を時間とともに表示します（要求された場合、以下を参照）。エージェントベースモデルは、[`abmplot`](@ref)と同様にプロットされ、アニメーション化され、`model`引数およびスプラットされた`kwargs`はそのまま伝播されます。この便利な関数は*集約されたエージェントデータ*にのみ機能します。

`abmexploration`を呼び出すと、`fig::Figure, abmobs::ABMObservable`が返されます。したがって、図を保存および/またはさらに修正することができ、収集されたデータ（ある場合）に`ABMObservable`を介してアクセスすることも可能です。

「リセット」ボタンをクリックすると、視覚的なガイダンスのためにデータプロットに赤い垂直線が追加されます。

## キーワード引数（`abmplot`のものに加えて）

  * `alabels, mlabels`: エージェントまたはモデルから`adata, mdata`でデータが収集されると、対応するプロットのyラベルは自動的に収集されたデータにちなんで名付けられます。また、`alabels, mlabels`（`adata, mdata`と正確に同じ長さの文字列ベクトル）を提供することも可能で、これらのラベルが代わりに使用されます。
  * `figure = NamedTuple()`: 作成されたFigureをカスタマイズするためのキーワード。
  * `axis = NamedTuple()`: 作成されたAxisをカスタマイズするためのキーワード。
  * `plotkwargs = NamedTuple()`: 結果の[`scatterlines`](https://makie.juliaplots.org/dev/examples/plotting_functions/scatterlines/index.html)プロットのスタイリングをカスタマイズするためのキーワード。

```
