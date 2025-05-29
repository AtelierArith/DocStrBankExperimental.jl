plotIDFCurves(model::DependentScalingModel, data::IDFdata; ...)

与えられたモデルに基づいてIDF曲線をプロットします。フィッティングを示すために、点ごとの推定値が追加されます（交差点）。期間とリターン期間はユーザーによって選択できますが、デフォルト値があります。show*confidence*intervals = trueの場合、点ごとの推定値に関連する95％信頼区間が表示されます。
