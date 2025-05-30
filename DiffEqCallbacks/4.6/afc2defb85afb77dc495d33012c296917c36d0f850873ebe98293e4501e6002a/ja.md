```
LinearizingSavingCallback(ils::IndependentlyLinearizedSolution)
LinearizingSavingCallback(ilss::Vector{IndependentlyLinearizedSolution})
```

保存コールバックを提供し、信号に補間点を挿入します。これにより、結果として保存された値の単純な線形補間が、解の高次補間の `abstol`/`reltol` 内に収まるようになります。これは本質的に時間/空間のトレードオフを作り出し、より多くの時間点が保存されることでメモリを多く消費しますが、補間は非常に安価であり、複数の補間タイプを気にする必要がないため、下流のアルゴリズムの複雑さが軽減されます。

アルゴリズムは内部で各時間点の間に3つの等間隔の点をチェックし、線形補間された関数に対するフィットの良さを判断します。これは4次までの補間には十分ですが、より高次の補間には良好なフィットを確保するためにより多くの点が必要になるかもしれません。これはまだ実装されていません。

このコールバックジェネレーターは、出力を格納するために `IndependentlyLinearizedSolution` オブジェクトを受け取ります。`IndependentlyLinearizedSolution` オブジェクト自体は、プライマル状態と共に線形化する導関数の数（ある場合）を制御します。

使用例:

```julia
ils = IndependentlyLinearizedSolution(prob)
solve(prob, solver; callback=LinearizingSavingCallback(ils))
```

# キーワード引数

  * `interpolate_mask::BitVector`: 積分器の補間関数を照会できる `u` インデックスのセット。偽のインデックスは、代わりに `sol.t` ポイントに基づいて線形補間されます（細分化なし）。これは、解が悪い振る舞いの補間のために特定のインデックスを無視する必要がある場合に便利です。
