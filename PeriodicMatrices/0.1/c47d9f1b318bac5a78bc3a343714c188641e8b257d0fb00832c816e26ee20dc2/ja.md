```
 ts2fm(A::Vector{<:AbstractMatrix}, period; method = "linear") -> At::Function
```

補間された行列時系列に対応する関数行列を計算します。与えられた行列時系列 `A` に対して、関数行列 `A(t)` はマッピング `A(t) = t -> Aint(t)` として定義され、ここで `Aint(t)` は [`Interpolations.jl`](https://github.com/JuliaMath/Interpolations.jl) パッケージで提供される補間オブジェクトの配列です。キーワードパラメータ `method` は、使用する補間方法を次のように指定します：

`method = "constant"` - 定常補間のための次数0の周期的Bスプラインを使用します；

`method = "linear"` - 線形補間のための次数1の周期的Bスプラインを使用します（デフォルト）；

`method = "quadratic"` - 二次補間のための次数2の周期的Bスプラインを使用します； 

`method = "cubic"` - 三次補間のための次数3の周期的Bスプラインを使用します。 
