`get_conflict(p::CMS)::Vector{CMSLit}`

現在の解における`p`の矛盾する変数を返します。これは`solve(p)`が呼び出され、`false`を返したことを前提としています。
