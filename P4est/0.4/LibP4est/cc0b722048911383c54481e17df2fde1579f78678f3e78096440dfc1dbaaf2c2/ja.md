ユーザー定義の [`p8est_iter_corner_t`](@ref) コールバックに利用可能な情報。

tree*boundary が false の場合、コーナーはツリーの内部にあります。tree*boundary が false の場合、sides[0] にはコーナーに接触する最も低い z-order 四分円が含まれます。tree*boundary が true の場合、その値はコーナーのツリーに対する位置に応じて P8EST*CONNECT_FACE/EDGE/CORNER になります。
