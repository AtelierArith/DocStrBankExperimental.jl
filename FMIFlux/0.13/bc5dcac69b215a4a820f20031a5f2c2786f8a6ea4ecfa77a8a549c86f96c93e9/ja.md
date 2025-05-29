非推奨:

ME-FMUに対して`fmiDoStep`に似た処理を行います（注意：fmiDoStepはCS-FMU専用です）。イベント処理（状態イベントおよび時間イベント）がサポートされています。イベントを処理したくない場合は、NeuralFMU `nfmu`の属性`eventHandling = false`を使用してイベント処理を無効にできます。

オプションとして、追加のFMU値はキーワード引数`setValueReferences`および`setValues`を介して設定できます。オプションとして、追加のFMU値はキーワード引数`getValueReferences`を介して取得できます。

関数は現在のシステム状態配列（"x"）を受け取り、状態導関数（"x dot"）の配列と、オプションで`getValueReferences`のFMU値を返します。引数`t`を介してFMU時間を設定することはオプションであり、設定されていない場合は、NeuralFMUの周りのODEソルバーの現在の時間が使用されます。
