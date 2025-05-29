```
rcsumsbal!(M; shift, r, c, maxiter, tol) -> (Dl,Dr)
```

非負行列 `M` をスケーリングするために Sinkhorn-Knopp のようなアルゴリズムを実行します。ここで、`Dl*M*Dr` の列の合計は正の行ベクトル `cs` に等しく、行の合計は正の列ベクトル `rs` に等しくなります。条件は `sum(c) = sum(r)` です。もし `shift = γ > 0` が指定されている場合、アルゴリズムはランク1の摂動 `M+γ*e1*e2` に対して実行されます。ここで、`e1` と `e2` は適切な次元の1のベクトルです。反復プロセスは、増分スケーリングが `tol` に近づいた時点で停止します。`maxiter` は許可される最大反復回数であり、`tol` は変換更新の許容誤差です。

結果として得られる `Dl*M*Dr` は `M` を上書きし、行の合計と列の合計が等しい行列になります。`Dl` と `Dr` は対角スケーリング行列です。

*注:* この関数は、ゼロ行またはゼロ列を持つ行列を処理するように修正された [1] の MATLAB 関数 `rowcolsums.m` に基づいています。実装されたシフトベースの正則化は [2] で提案されています。

[1] F.M.Dopico, M.C.Quintana and P. van Dooren, "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022.

[2] P.A.Knight, The Sinkhorn–Knopp algorithm: Convergence and applications, SIAM J. Matrix Anal. Appl., 30 (2008), pp. 261–275.
