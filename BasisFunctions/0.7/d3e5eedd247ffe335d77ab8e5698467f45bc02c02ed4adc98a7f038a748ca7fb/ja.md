辞書のメンバ関数は、`eval_element` ルーチンを使用して評価されます。このルーチンは、辞書、メンバ関数のインデックス、および評価する点を引数として受け取ります。

この関数は、インデックスの範囲チェックを行い、また点 x が関数のサポート内にあるかどうかを確認します。範囲外のインデックスに対しては `BoundsError` がスローされます。x がサポートの外にある場合は、値 `0` が返されます。

インデックスのチェックの後、関数は `unsafe_eval_element1` を呼び出します。この関数は、x がサポート内にあるかどうかを確認し、その後 `unsafe_eval_element` を呼び出します。後者の関数は具体的な辞書によって実装されるべきです。範囲チェックやサポートチェックを回避したいユーザーは、それぞれ `eval_element` または `unsafe_eval_element1` をインターセプトすることができます。
