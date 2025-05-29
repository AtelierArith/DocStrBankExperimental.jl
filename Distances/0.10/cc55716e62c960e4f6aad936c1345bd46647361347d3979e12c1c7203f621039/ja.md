Bregmanダイバージェンスを実装します。これについての親しみやすい紹介は[こちら](http://mark.reid.name/blog/meet-the-bregman-divergences.html)で見つけることができます。Bregmanダイバージェンスは「平均最小化」特性の最小限の実装です。

（凸微分可能な）関数Fは、ベクトル（任意のタイプまたはサイズ）を実数にマッピングすることが想定されています。使用される内積は`Base.dot`ですが、`inner`を定義するか、キーワード引数を渡すことで、どちらでも渡すことができます。解析的勾配が利用できない場合、Juliaは優れた自動微分パッケージのスイートを提供しています。

```julia
function evaluate(dist::Bregman, p::AbstractVector, q::AbstractVector)
```
