```
MorisitaOverlap(q::Int)
```

MorisitaOverlap距離を作成します。これは、q-グラムから作成された辞書にも使用できる一般的な統計的分散測定です。詳細は https://en.wikipedia.org/wiki/Morisita%27s*overlap*index を参照してください。これは、文字列に含まれるq-グラムだけでなく、q-グラムごとのカウントに基づいているため、他の多くのQGramDistancesよりも詳細です。

距離は次のように対応します。

$$
(2 * sum(m(s1) .* m(s2)) / (sum(m(s1).^2)*M(s2)/M(s1) + sum(m(s2).^2)*M(s1)/M(s2))
$$

ここで、$m(s)$は文字列$s$のq-グラムカウントのベクトルであり、$M(s)$はそれらのカウントの合計です。
