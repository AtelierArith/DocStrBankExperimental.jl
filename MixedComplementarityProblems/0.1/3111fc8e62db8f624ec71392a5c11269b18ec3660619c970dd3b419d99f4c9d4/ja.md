基本的な内部点ソルバーで、Nocedal & Wrightの第19章に基づいています。緩和されたプライマル・双対システムを解くことによってステップ方向`δz`を計算します。すなわち、∇F(z; ϵ) δz = -F(z; ϵ)です。

ステップ方向`δz`が与えられた場合、「境界への割合」ラインサーチを実行します。すなわち、`(x, s)`に対して、ステップサイズ`α_s`を次のように選択します。               α*s = max(α ∈ [0, 1] : s + α δs ≥ (1 - τ) s) そして`y`に対して、ステップサイズ`α*s`を次のように選択します。               α_y = max(α ∈ [0, 1] : y + α δy ≥ (1 - τ) y)。

τの典型的な値は0.995です。||F(z; ϵ)|| ≤ ϵに収束したら、通常はϵを0.1または0.2の因子で減少させ、前のサブプロブレムがより少ない反復で解かれた場合は、より小さい値を選択します。

位置引数:     - `mcp::PrimalDualMCP`: 解くべき混合補完問題。     - `θ::AbstractVector{<:Real}`: パラメータベクトル。

キーワード引数:     - `x₀::AbstractVector{<:Real}`: 初期プライマル変数。     - `y₀::AbstractVector{<:Real}`: 初期双対変数。     - `s₀::AbstractVector{<:Real}`: 初期スラック変数。     - `ϵ₀::Real`: 初期緩和スケール。     - `tol::Real = 1e-4`: KKT誤差の許容誤差。     - `max_inner_iters::Int = 20`: 最大内側反復回数。     - `max_outer_iters::Int = 50`: 最大外側反復回数。     - `tightening_rate::Real = 0.1`: 許容誤差を厳しくする速度。     - `loosening_rate::Real = 0.5`: 許容誤差を緩める速度。     - `min_stepsize::Real = 1e-2`: ラインサーチの最小ステップサイズ。     - `verbose::Bool = false`: デバッグ情報を印刷するかどうか。     - `linear_solve_algorithm::LinearSolve.SciMLLinearSolveAlgorithm`: 使用する線形解法アルゴリズム。`LinearSolve.jl`の任意のソルバーを使用できます。
