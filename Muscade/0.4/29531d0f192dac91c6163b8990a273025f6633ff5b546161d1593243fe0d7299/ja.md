```
matrix = studysingular(state;SP,[iclasses=(Λ,:X,:U,:A)],[jclasses=iclasses],[verbose::𝕓=true],[dbg=(;)])
```

`state`に対して必要なクラスに対応する増分行列を生成し、行列の零空間について報告します。

そのために、増分行列はフルフォーマットに変換され、小さなモデルに適用可能性が制限されます。

関数は増分行列を返します。
