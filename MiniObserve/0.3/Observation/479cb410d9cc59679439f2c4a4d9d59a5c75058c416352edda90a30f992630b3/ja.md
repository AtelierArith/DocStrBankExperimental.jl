```Julia
@observe(statstype, user_arg1 [, user_arg2...], declarations)
```

データ構造のセットに対する完全な分析およびロギングスイートを生成します。

Observeは（新しい）型名、いくつかのユーザー引数、および宣言のブロックを期待します。ユーザー引数を受け取り、データ型のインスタンスを返す`observe`関数を生成します。宣言ブロックは`observe`関数の本体にそのままコピーされますが、「擬似マクロ」`@record`および`@stat`のすべての出現は、対応する分析コードに置き換えられます。

新しく定義された結果データ型は、すべての計算結果のプロパティを含みます。

したがって、次の宣言が与えられた場合

```Julia
@observe Data model stat1 stat2 begin
	@record "time"      model.time
	@record "N"     Int length(model.population)

	for ind in model.population 
		@stat("capital", MaxMinAcc{Float64}, MeanVarAcc{FloatT}) <| ind.capital
		@stat("n_alone", CountAcc)           <| has_neighbours(ind)
	end

	@record s1			stat1
	@record s2			stat1 * stat2
end
```

次のメンバーを提供する型Dataが生成されます：

```Julia
struct Data
	time :: Float64
	N :: Int
	capital :: @NamedTuple{max :: Float64, min :: Float64, mean :: Float64, var :: Float64}
	n_alone :: @NamedTuple{N :: Int}
	s1 :: Float64
	s2 :: Float64
end
```

このマクロはまた、必要な計算を実行し、`Data`オブジェクトを返す`observe(::Type{Data), model, stat1, stat2)`メソッドも作成します。

`print_header`を使用して生成された型のヘッダーを出力に印刷し、`log_results`を使用してデータオブジェクトの内容を印刷します。
