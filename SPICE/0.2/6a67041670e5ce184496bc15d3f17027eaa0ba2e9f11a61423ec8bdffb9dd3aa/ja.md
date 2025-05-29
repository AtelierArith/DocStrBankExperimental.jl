```
spkw15(handle, body, center, frame, first, last, segid,
       epoch, tp, pa, p, ecc, j2flg, pv, gm, j2, radius)
```

SPKファイルにタイプ15セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: 軌道対象のボディコード
  * `center`: ボディの運動の中心のボディコード
  * `frame`: 状態の基準フレーム
  * `first`: 状態を計算できる最初の有効時間
  * `last`: 状態を計算できる最後の有効時間
  * `segid`: セグメント識別子
  * `epoch`: ペリapsisのエポック
  * `tp`: 軌道極ベクトル
  * `pa`: ペリapsisベクトル
  * `p`: 半ラテスレクトム
  * `ecc`: 離心率
  * `j2flg`: J2処理フラグ
  * `pv`: 中心ボディ極ベクトル
  * `gm`: 中心ボディのGM
  * `j2`: 中心ボディのJ2
  * `radius`: 中心ボディの赤道半径

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw15_c.html)
