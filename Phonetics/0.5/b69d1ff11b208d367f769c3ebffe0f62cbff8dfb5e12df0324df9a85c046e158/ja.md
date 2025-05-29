```
avgseq(S::Array{Sound}, rep=:mfcc; [method=:dtw, dist=SqEuclidean(), radius=10, center=:medoid, dtwradius=nothing, progress=false])
```

`S`内の`Sound`オブジェクトを`rep`で指定された表現に変換し、それらの平均シーケンスを見つけます。現在、`rep`には`:mfcc`のみがサポートされており、`MFCC`パッケージのデフォルトを使用しますが、各フレームの最初の係数は削除され、そのフレーム内のフィルタバンクの対数エネルギーの合計に置き換えられます。これはASRで標準的な方法です。
