ソース: FMISpec3.0, バージョン D5ef1c1: 2.2.12. 連続出力の導関数を取得する

出力値の n 番目の導関数を取得します。

valueReferences - 導関数を取得する変数を定義する値参照のベクトルです。変数の複数の導関数を取得する場合は、値参照を複数回リストしてください。

nValueReferences - 引数 valueReferences と orders の次元です。

orders - 各導関数の次数を含みます（1 は1階導関数、2 は2階導関数、…、0 は許可されていません）。変数の複数の導関数を取得する場合は、valueReferences 配列内の複数回出現する値参照に対応するように、orders 配列にそれらのリストを提供してください。取得可能な導関数の最高次数は、ModelDescription 内の 'maxOutputDerivativeOrder' タグによって決定できます。

values - 導関数の値を持つベクトルです。values 要素の順序は、二重直列化から導出されます: 外側のレベルは値参照の組み合わせ（例: valueReferences[k]）と次数（例: orders[k]）に対応し、内側のレベルはセクション 2.2.6.1 で定義された変数の直列化に対応します。内側のレベルはスカラー変数には存在しません。

nValues - 引数 values のサイズです。nValues は、すべての対応する出力変数がスカラー変数である場合にのみ nValueReferences に等しくなります。
