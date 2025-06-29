```
TFIDF(
    data::DataAccessor,
    tf::AbstractMatrix,
    idf::AbstractMatrix
)
```

TF-IDFスコアリングを使用したコンテンツベースの推薦。TFとIDFの行列はそれぞれ`tf`と`idf`として指定されます。

より具体的には、各アイテムは単語のセットとして表現され、アイテムは単語のTF-IDF重み付けによってモデル化されます。この技術は、文書-単語行列をモデル化するために情報検索で最初に使用されました。アイテム-単語行列の場合、特定のアイテム$i$に対する用語$t$の出現頻度（TF）は次のように定義されます。

$$
\mathrm{tf}(t, i) = \frac{n_{t,i}}{N_i},
$$

ここで、$n_{t,i}$は$I$の$(i, t)$要素を示し、$N_i$はアイテム$i$が含む単語の総数です。したがって、$\mathrm{tf}(t, i)$は用語の正規化された頻度によってアイテム-用語ペアを特徴付けます。一方、逆文書頻度（IDF）は$M$アイテムに対して次のように計算されます。

$$
\mathrm{idf}(t) = \log \frac{M}{\mathrm{df}(t)} + 1,
$$

ここで、$\mathrm{df}(t)$は用語$t$に関連するアイテムの数をカウントします。$\mathrm{idf}(t)$の役割は、一般的な単語が特定のアイテムを特徴付けることができないため、一般的に使用される用語の影響を減少させることです。

最後に、各アイテム-用語ペアはTF-IDFスキームにおいて$\mathrm{tf}(t, i) \cdot \mathrm{idf}(t)$によって重み付けされます。たとえば、ユーザーにウェブページを推薦したい場合、まずページ上の文を解析し、次に各用語の頻度に基づいてベクトルを構築する必要があります。同様に、レコメンダーがフォークソノミー（すなわち、ソーシャルタグ付け）サービスで実行されている場合、タグの頻度はベクトルの各次元に対応し、$\mathrm{tf}(t, i)$と$\mathrm{idf}(t)$は最終的に各アイテム-タグペアに対して計算されます。

![tfidf](./assets/images/tfidf.png)
