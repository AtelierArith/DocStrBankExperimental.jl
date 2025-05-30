ソース: FMISpec2.0.2[p.48]: 2.2.7 モデル変数の定義 (ModelVariables)

変数がどのように初期化されるかを定義する列挙型。因果関係が "input" または "independent" の場合、initial に値を提供することは許可されていません：

"exact": 変数は、Real、Integer、Boolean、String または Enumeration の下で提供された開始値で初期化されます。 "approx": 変数は代数ループの反復変数であり、初期化時の反復は開始値から始まります。 "calculated": 変数は初期化中に他の変数から計算されます。 "start" 値を提供することは許可されていません。 initial が存在しない場合、因果関係と変動性に基づいて以下の表によって定義されます。 initial = exact または approx、または因果関係 = "input" の場合、開始値を提供する必要があります。 initial = calculated または因果関係 = "independent" の場合、開始値を提供することは許可されていません。 causality = "input" の変数に対して fmiSetXXX が呼び出されない場合、FMU はこの入力の値として開始値を使用する必要があります。 列挙型の定数の再定義を助けるために、接頭辞 "fmi2" が追加されました。
