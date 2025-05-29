excitation*duration(m, r*ps::U, src::SourceParameters{S,T}, rvt::RandomVibrationParameters) where {S<:Float64,T<:Real,U<:Real}

汎用関数は励起持続時間モデルを実装しています。

現在、一般的なBoore & Thompson (2014, 2015)モデルのみが実装されており、エドワーズ（2023）による南アフリカ向けのプロジェクト特有のモデルと、2つの英国の持続時間モデルも含まれています。最初の2つはBoore & Thompson (2015)の論文内で表現されているため、`rvt.dur_region`に基づいてパス持続時間を切り替えるだけです。エドワーズモデルを有効にするには、`rvt.dur_ex == :BE23`を使用します。英国モデルを使用するには、`rvt.dur_ex == :UKfree`または`rvt.dur_ex == :UKfixed`を使用します。
