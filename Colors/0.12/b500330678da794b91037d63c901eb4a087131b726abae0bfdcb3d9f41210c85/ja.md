```
colormatch(wavelength)
colormatch(matchingfunction, wavelength)
```

CIE標準観察者の色合せ関数を評価します。

# 引数

  * `matchingfunction`（オプション）：合せ関数を指定するために使用される型。選択肢には以下が含まれます：

      * `CIE1931_CMF`（デフォルト、CIE 1931 2°合せ関数）
      * `CIE1964_CMF`（CIE 1964 10°色合せ関数）
      * `CIE1931J_CMF`（`CIE1931_CMF`へのジャッド調整）
      * `CIE1931JV_CMF`（`CIE1931_CMF`へのジャッド-ボス調整）
      * `CIE2006_2_CMF`（CIE 2006 2° LMSコーン基礎から変換）
      * `CIE2006_10_CMF`（CIE 2006 10° LMSコーン基礎から変換）
  * `wavelength`：刺激の波長（ナノメートル単位）。

知覚された色のXYZ値を返します。

!!! note
    2020年2月現在、`CIE1931_CMF`と`CIE1964_CMF`のみがISO/CIEによって標準化されています。`CIE2006_2_CMF`と`CIE2006_10_CMF`は、CIEによってまだ承認されていない提案であり、時折CIE 2012 CMFと呼ばれることがあります。

