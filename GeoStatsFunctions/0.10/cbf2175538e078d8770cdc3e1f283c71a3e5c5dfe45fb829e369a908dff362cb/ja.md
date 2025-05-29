```
funplot(f; [options])
```

与えられた `options` で地質統計関数 `f` をプロットします。

## 一般的なオプション:

  * `color`  - 色
  * `size`   - サイズ（線の太さ）
  * `maxlag` - 最大ラグ
  * `labels` - 変数名

## 経験的関数オプション:

  * `style`       - スタイル（線のスタイル）
  * `pointsize`   - 点のサイズ
  * `showtext`    - テキストカウントを表示
  * `textsize`    - テキストカウントのサイズ
  * `showhist`    - ヒストグラムを表示
  * `histcolor`   - ヒストグラムの色

### 注意

この関数は、Julia v1.9以降の言語のパッケージ拡張を介してMakie.jlバックエンドが存在する場合にのみ機能します。
