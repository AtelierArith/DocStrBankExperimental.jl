wbgt(diurnal*temperature::ClimGrid, vapor*pressure::ClimGrid)

日中の気温（摂氏）とその日の水蒸気圧（Pa）を使用して計算された簡略化された湿球グローバル温度（*wbgt*）（摂氏）を返します。これは、7:00（午前7時）から17:00（午後5時）までの平均日中気温です。

$$
wbgt = 0.567 * Tday + 0.00393 * vp + 3.94
$$
