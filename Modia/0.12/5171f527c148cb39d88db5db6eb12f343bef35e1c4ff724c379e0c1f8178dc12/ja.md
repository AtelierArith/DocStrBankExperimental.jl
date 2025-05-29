```
xe_info = StateElementInfo(x_name, x_name_julia, der_x_name, der_x_name_julia,
                           stateCategory, unit, startOrInit, fixed, nominal, unbounded;
                           startIndex=-1, x_segmented_startIndex=-1)
```

状態ベクトルの1要素の情報を定義する可変構造体`StateElementInfo`のインスタンスを返します。

# 引数

  * x_name: x要素の名前、または名前がない場合は""（stateCategory = XLAMBDAまたはXMUEの場合）
  * x*name*julia: getDerivatives!/getResiduals!関数内のx要素のJulia名、または必要ない場合は""（コード生成がないため）。
  * der*x*name: der*x要素の名前、または`der(x*name)`の場合、または名前がない場合は""（stateCategory = XALGの場合）。
  * der*x*name*julia: getDerivatives!/getResiduals!関数内のder*x要素のJulia名、または必要ない場合は""（コード生成がないため）。
  * stateCategory::StateCategory: 状態のカテゴリ
  * unit: XD、XALG（x*name）またはXLAMBDA、XMUE（der*x_name）の単位、またはまだ知られていない場合は""。
  * startOrInit: 開始または初期値（スカラーまたはベクトル）
  * fixed: false（=推測値）またはtrue（=初期化によって変更されない）。ode=falseの場合のみ関連し、それ以外は無視されます。
  * nominal: 名目値（startOrInit値を介して決定された場合はNaN）
  * unbounded: falseまたはtrue
  * startIndex: -1（まだ知られていない場合）。xに関するstartIndex。
  * x*segmented*startIndex: -1（まだ知られていない場合）。x_segmentedに関するstartIndex。
