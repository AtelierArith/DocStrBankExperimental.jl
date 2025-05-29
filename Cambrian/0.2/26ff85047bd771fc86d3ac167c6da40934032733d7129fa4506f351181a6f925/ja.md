mutate(parent::BoolIndividual, m*rate::Float64). 使用するには、mutate(parent::BoolIndividual) = mutate(parent, m*rate) を定義し、Boolean 個体のために設定された m_rate で、これにより親のビットがランダムに反転します。
