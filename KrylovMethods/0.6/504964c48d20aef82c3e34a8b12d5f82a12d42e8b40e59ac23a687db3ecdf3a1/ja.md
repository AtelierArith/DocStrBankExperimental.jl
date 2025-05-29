x = ssorPrecTrans!(A::SparseMatrixCSC,X::Array,B::Array,OmInvD::Vector=1 ./diag(A))

対称行列 A に対して、線形システム A*X = B に SSOR ステップを適用します。効率のため、行列 A の転置で動作します。

入力:

A       - 疎行列 CSC、ここでは対称であると仮定   X       - 現在の反復値   R       - 残差    OmInvD  - 重み付き対角行列、すなわち、omega./diag(A)

出力: このメソッドは X を変更し、リアルタイムで動作します。配列 B は変更されません。

このバージョンは、例えば CG の前処理器として非常に適しています。

A*X=B を解くための例、A が疎対称正定値の場合:     omega = 1.2;     d = omega./diag(A);     x = zeros(length(d)) # 前処理器の結果のための事前割り当て。     PC(r) = (x[:]=0.0; return ssorPrecTrans!(A,x,r,d));     y = KrylovMethods.cg(A,b,tol=1e-12,maxIter=200,M=PC,out=1)[1]
