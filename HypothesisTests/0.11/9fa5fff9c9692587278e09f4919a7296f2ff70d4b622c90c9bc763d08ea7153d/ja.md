```
ADFTest(y::AbstractVector{T}, deterministic::Symbol, lag::Int) where T<:Real
```

拡張ディッキー・フラー単位根検定を計算します。

`y` はテストされる時系列であり、`deterministic` は決定論的項を決定します（オプション: `:none`, `:constant`, `:trend`, `:squared_trend`）、`lag` はテスト回帰に含まれる遅れた一次差分の数をそれぞれ示します。

臨界値と漸近p値は、MacKinnon (2010) および MacKinnon (1994) に従った応答面回帰に基づいて計算されます。これらは、異なるアルゴリズムが使用される可能性があるため、他の回帰パッケージで報告されているものとわずかに異なる場合があります。

# 参考文献

  * James G. MacKinnon, 2010, "Critical values for cointegration tests," QED Working Paper No. 1227, 2010, [link](http://ideas.repec.org/p/qed/wpaper/1227.html).
  * James G. MacKinnon, 1994, "Approximate Asymptotic Distribution Functions for Unit-Root and Cointegration Tests", Journal of Business & Economic Statistics, Vol. 12, No. 2, pp. 167-176, [link](http://www.jstor.org/stable/1391481).

# 外部リンク

  * [拡張ディッキー・フラー検定 - Wikipedia](https://en.wikipedia.org/wiki/Augmented_Dickey–Fuller_test)
