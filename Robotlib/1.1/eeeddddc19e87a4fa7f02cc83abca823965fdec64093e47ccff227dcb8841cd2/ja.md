```
T_TF_S, meanRMS,RMS, norms = calibNAXP(points_S, lines_S, POSES, T_TF_S, planes::AbstractVector{Int},  iters = 50; doplot=false)
```

この関数は、「平面制約を使用した2D測定からの6自由度目と手のキャリブレーション」という論文のアルゴリズムを実装しており、問題 `Prb = n'A(X*Ps)` を解決します。アルゴリズムへの拡張は、論文「物理システムにおける推定のための機械学習とシステム同定」の第13.2章および付録で開発されました。 https://lup.lub.lu.se/search/publication/ffb8dc85-ce12-4f75-8f2b-0881e492f6c0

結果が悪い場合は、データが正しい形式で送信されているか確認してください。

`POSES ∈ R(4,4,N)` は常にロボットFKからのツールフレームの位置です。

`points_S ∈ R(3,N)` はラインレーザースキャナーからの測定値です。センサーフレームで与えられます。このスクリプトは、レーザープレーンがセンサーのXY平面であり、y軸がセンサーから外向きに指していると仮定しています。

`lines_S ∈ R(3,N)` は、測定されたレーザーラインの方向に対応するベクトルです。`planes ∈ Z(N)` は、測定がどの平面から来ているかに対応するインデックスのベクトルです。`points_S` と同じ長さでなければならず、平面を1から始めて列挙します。例（N=15、平面の数=3）： [1,1,1,1,1,2,2,2,2,2,3,3,3,3,3]

`iters` は反復回数を決定します。

@inproceedings{carlson2015six,   title={Six DOF eye-to-hand calibration from 2D measurements using planar constraints},   author={Carlson, Fredrik Bagge and Johansson, Rolf and Robertsson, Anders},   booktitle={Intelligent Robots and Systems (IROS), 2015 IEEE/RSJ International Conference on},   pages={3628–3632},   year={2015},   organization={IEEE} }
