```
textcurvecentered(the_text, the_angle, the_radius, center::Point;
      clockwise = true,
      letter_spacing = 0,
      baselineshift = 0
```

このバージョンの `textcurve()` 関数は、円の周りに配置する必要がある短いテキスト文字列のために設計されています。（ヒップスターブランドやレトロナウツに非常に愛されているチーズのような効果です。）

`letter_spacing` は文字間のトラッキング/スペースを調整し、タイトな場合は (-)、ルーズな場合は (+) です。`baselineshift` はテキストをベースラインから上または下に移動させます。

`textcurvecentred`（UKスペル）は同義語です。
