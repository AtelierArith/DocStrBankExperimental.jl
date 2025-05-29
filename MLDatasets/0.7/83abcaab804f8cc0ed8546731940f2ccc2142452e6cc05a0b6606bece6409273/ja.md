```
UD_English(; split=:train, dir=nothing)
UD_English(split=; [dir])
```

英語のためのゴールドスタンダードユニバーサル依存関係コーパスで、英語ウェブツリーバンクLDC2012T13のソース資料に基づいて構築されています (https://catalog.ldc.upenn.edu/LDC2012T13)。

このコーパスは、254,825語と16,621文から成り、ウェブメディアの5つのジャンル（ウェブログ、ニュースグループ、電子メール、レビュー、Yahoo!の回答）から取得されています。文のソースに関する詳細はLDC2012T13のドキュメントを参照してください。木構造は自動的にスタンフォード依存関係に変換され、その後ユニバーサル依存関係に手動で修正されました。すべての基本的な依存関係の注釈は単一注釈されており、その一部は二重注釈されています。また、一貫性を向上させるためにその後の修正が行われました。ユニバーサルPOS、特徴、および強化された依存関係など、ツリーバンクの他の側面は主に自動的に行われており、手動修正は非常に限られています。

著者: Natalia Silveira、Timothy Dozat、Marie-Catherine de Marneffe、Samuel Bowman、Miriam Connor、John Bauer、Christopher D. Manning ウェブサイト: https://github.com/UniversalDependencies/UD_English-EWT
