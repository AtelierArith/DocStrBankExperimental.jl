ソース: FMISpec3.0, バージョン D5ef1c1: 2.2.11. 部分導関数の取得

この関数は、FMUの随伴導関数 v^T*{sensitivity}= v^T*{seed} ⋅ J を計算します。

unknowns - 不明な値の参照を含みます。

nUnknowns - 引数 unknowns の長さを含みます。

knowns - 知られている値の参照を含みます。

nKnowns - 引数 knowns の長さを含みます。

seed - シードベクトルの成分を含みます。

nSeed - seed の長さを含みます。

sensitivity - 感度ベクトルの成分を含みます。

nSensitivity - sensitivity の長さを含みます。

この関数は、ModelDescription の 'ProvidesAdjointDerivatives' タグが設定されている場合にのみ呼び出すことができます。
