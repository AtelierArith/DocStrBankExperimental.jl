||Q||, ||Q^2||, ... ||Q^m|| のノルムを U^0 で推定します。

U は行列 [ones(1,n-1); -I_(n-1,n-1)] です。現在、f*U==0（すなわち、f のすべての要素が等しい）と仮定されています。

f は区間ベクトルでなければなりません。

次の定数はキーワード引数として指定できます：

normQ, normE, normv0, normEF, normIEF, normN

そうでなければ、計算されます（これは遅くなる可能性があります）。

e と f は is*integral*preserving==false の場合に指定する必要があります。is*integral*preserving が true の場合、指定することはできますが、その場合は無視されます。
