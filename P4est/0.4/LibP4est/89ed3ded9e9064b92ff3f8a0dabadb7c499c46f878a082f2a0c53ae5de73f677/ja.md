"ポイント"と四分円の一致を照会するコールバック関数。

この関数は2つの役割で呼び出すことができます：四分円ごと、つまりパラメータ **point** が NULL の場合、またはポイントごと、四分円ごとに複数回呼び出される可能性があります。

### パラメータ

  * `p4est`:[in] 照会されるフォレスト。
  * `which_tree`:[in] 考慮中のツリーID。
  * `quadrant`:[in] 考慮中の四分円。この四分円は、フォレストに含まれる四分円よりも粗い場合（祖先の場合）、一時変数でありフォレストストレージの一部ではありません。そうでない場合は、葉であり、フォレストストレージに直接ポイントします。
  * `local_num`:[in] 四分円が葉でない場合、これは < 0 です。そうでない場合は、プロセッサローカルストレージに対する四分円の（非負の）インデックスです。
  * `point`:[in] "ポイント"の表現；ユーザー定義。**point** が NULL の場合、コールバックは四分円関連の検索メタデータを準備するために使用される可能性があります。

### 戻り値

**point** が NULL の場合、**quadrant** に制限された検索を実行すべきなら true、スキップするなら false。そうでない場合、ポイントが四分円に含まれる可能性があるなら true、そうでないなら false；戻り値は葉には影響しません。
