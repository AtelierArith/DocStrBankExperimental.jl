tree_polish!(newt, models; tol = 10^-4, verbose = 1, topology = true)

木とモデル関数を取り、枝の長さを最適化し、オプションでトポロジーも最適化します。最終的な対数尤度（LL）を返します。出力を抑制するには `verbose=0` を設定してください。注意: これは徹底的な木の探索を意図したものではなく（異なるヒューリスティックが必要）、すでに最適に比較的近い木を磨くためのものです。
