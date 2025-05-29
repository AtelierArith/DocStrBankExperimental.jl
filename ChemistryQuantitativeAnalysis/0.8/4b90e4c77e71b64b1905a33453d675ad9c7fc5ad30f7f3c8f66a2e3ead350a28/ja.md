```
Batch(dt::AbstractDataTable; 
    signal = :area, 
    rel_sig = :relative_signal, 
    est_conc = :estimated_concentration, 
    true_conc = :true_concentration, 
    acc = :accuracy, 
    calid = r"Cal_(\d)_(\d*-*\d*)", 
    order = "LR", 
    ratio = nothing, 
    df = nothing, 
    f2c = 1,
    parse_decimal = x -> replace(x, "-" => "."))
```

データからバッチを構築します。すべての分析物は通常の分析物と見なされるため、キャリブレーションカーブはすぐには構築されません。`batch.method.analytetable`でisdとキャリブレーション設定を確認した後に`init_calibration!`を呼び出してください。

# 引数

  * `dt`: キャリブレーションカーブとサンプルの両方を含むデータ。

# キーワード引数

  * `signal`: 実験取得データのタイプとキー名、例: `:area`。
  * `rel_sig`: 相対信号のキー名。
  * `est_conc`: 推定濃度のキー名。
  * `true_conc`: 真の濃度のキー名。
  * `acc`: 精度のキー名。
  * `calid`: キャリブレーションポイントの識別子。2つの可能な値があります。

      * `Regex`、レベルおよび濃度に関連する要因（濃度の比率または希釈係数）をキャプチャする必要があります。前者は整数として直接解析できる必要があります。後者は`parse_decimal`を適用した後に浮動小数点数として解析できる必要があります。
      * `Vector`、各サンプルに番号（キャリブレーションレベル）、`missing`または`nothing`（通常のサンプル）を割り当てます。
  * `order`: `String`、キャプチャされた文字列の順序と識別を表します。`L`はレベル、`R`は濃度の比率、`D`は希釈係数（df）です。
  * `ratio`: 各レベルの濃度の比率。`nothing`はキャプチャされた値を使用することを示します。
  * `df`: 各レベルの希釈係数。`nothing`はキャプチャされた値を使用することを示します。
  * `f2c`: `Number`または数値のベクトル；濃度はf2c * ratioまたはf2c / dfに等しいです。ベクトルが提供されると、各要素は各分析物の`f2c`値を表します。
  * `parse_decimal`: `Function`、文字列を浮動小数点数として解析できる別の文字列に変換します。
