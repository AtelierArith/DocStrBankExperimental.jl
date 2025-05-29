ユーザー定義の[`p4est_iter_corner_t`](@ref)コールバックに利用可能な情報。

tree*boundaryがfalseの場合、コーナーはツリーの内部にあります。tree*boundaryがfalseの場合、sides[0]にはコーナーに接触する最も低いz-orderの四分円が含まれます。tree*boundaryがtrueの場合、その値はコーナーのツリーに対する位置に応じてP4EST*CONNECT_FACE/CORNERになります。
