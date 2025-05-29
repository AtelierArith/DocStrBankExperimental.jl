```
distinctiveness(s::Sound, corpus::Array{Sound}, rep=:mfcc; [method=:dtw, dist=SqEuclidean(), radius=10, reduction=mean])
```

`s`と`corpus`を`rep`で指定された表現に変換し、`corpus`を考慮した`s`の音響的独自性を計算します。現在、`rep`には`:mfcc`のみがサポートされており、`MFCC`パッケージのデフォルトを使用しますが、各フレームの最初の係数は削除され、そのフレーム内のフィルタバンクの対数エネルギーの合計に置き換えられます。これはASRで標準的な方法です。
