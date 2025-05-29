shi_tomasi - Shi - Tomasi コーナー検出器

```
Usage:               cimg = shi_tomasi(img, sigma=1)
             (cimg, r, c) = shi_tomasi(img, sigma=1; args...)

Arguments:   
           img    - 処理する画像。
                    ::Array{T,2} または ::ImageMeta{T,2} 
           sigma  - ガウス和ウィンドウの標準偏差。 
                    使用する典型的な値は1-3です。デフォルトは1です。
Keyword arguments:
          args... - 非最大抑制を行うためのキーワード引数のシーケンス。
                    これらは次の通りです（詳細はnonmaxsuppts()を参照）
           radius - 非最大抑制で考慮される領域の半径。
                    使用する典型的な値は1-3ピクセルです。デフォルト（および最小値）は1です。
           thresh - 閾値、閾値より大きい値を持つ特徴のみが返されます。デフォルトは0です。
                N - 返す最大特徴数。この場合、'thresh'を超える値を持つ
                    N個の最も強い特徴が返されます。デフォルトはInfです。
         subpixel - trueに設定すると、特徴がサブピクセル精度で局所化されます。デフォルトはfalseです。
             img  - オプションの画像データ。画像が提供されると、
                    検出されたコーナーがこの画像にオーバーレイされます。これは
                    パラメータ調整に役立ちます。デフォルトは[]です。

Returns:
           cimg   - コーナー強度画像。
           r      - コーナーポイントの行座標。
           c      - コーナーポイントの列座標。
```

入力がImageMetaの場合、cimgはプロパティspatialorderが["y","x"]に設定されたImageMetaとなり、r、cで返される座標と一貫性が保たれます。

キーワード引数が提供されていない場合、'cimg'のみが生のコーナー強度画像として返されます。その後、'cimg'内の値を確認して、使用する適切な閾値を決定することができます。

Shi - Tomasi測定は構造テンソルの最小固有値を返します。これは、HarrisおよびNoble検出器が近似しようとする理想を表しています。1988年、Harrisは特徴を計算する際に平方根を取る計算コストを避けたいと考えていました。これは今日ではもはや関連性がありません！

See also: harris(), noble(), hessianfeatures(), structuretensor(), nonmaxsuppts(), derivative5()
