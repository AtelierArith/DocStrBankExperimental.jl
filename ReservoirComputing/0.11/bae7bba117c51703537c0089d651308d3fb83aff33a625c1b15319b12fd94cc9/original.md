```
HybridESN(model, train_data, in_size, res_size; kwargs...)
```

Construct a Hybrid Echo State Network (ESN) model that integrates traditional Echo State Networks with a predefined knowledge model [^Pathak2018].

# Parameters

  * `model`: A `KnowledgeModel` instance representing the knowledge-based model to be integrated with the ESN.
  * `train_data`: The training dataset used for the ESN. This data can be preprocessed or raw data depending on the nature of the problem and the preprocessing steps considered.
  * `in_size`: The size of the input layer, i.e., the number of input units to the ESN.
  * `res_size`: The size of the reservoir, i.e., the number of neurons in the hidden layer of the ESN.

# Optional Keyword Arguments

  * `input_layer`: A function to initialize the input matrix. Default is `scaled_rand`.
  * `reservoir`: A function to initialize the reservoir matrix. Default is `rand_sparse`.
  * `bias`: A function to initialize the bias vector. Default is `zeros32`.
  * `reservoir_driver`: The driving system for the reservoir. Default is an RNN model.
  * `nla_type`: The type of non-linear activation used in the reservoir. Default is `NLADefault()`.
  * `states_type`: Defines the type of states used in the ESN. Default is `StandardStates()`.
  * `washout`: The number of initial timesteps to be discarded in the ESN's training phase. Default is 0.
  * `rng`: Random number generator used for initializing weights. Default is `Utils.default_rng()`.
  * `T`: The data type for the matrices (e.g., `Float32`).
  * `matrix_type`: The type of matrix used for storing the training data. Default is inferred from `train_data`.

[^Pathak2018]: Jaideep Pathak et al. "Hybrid Forecasting of Chaotic Processes: Using Machine Learning in Conjunction with a Knowledge-Based Model" (2018).
