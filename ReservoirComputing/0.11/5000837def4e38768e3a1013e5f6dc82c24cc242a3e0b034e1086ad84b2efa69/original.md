KnowledgeModel(prior_model, u0, tspan, datasize)

Constructs a `Hybrid` variation of Echo State Networks (ESNs) [^Pathak2018] integrating a knowledge-based model (`prior_model`) with ESNs.

# Parameters

  * `prior_model`: A knowledge-based model function for integration with ESNs.
  * `u0`: Initial conditions for the model.
  * `tspan`: Time span as a tuple, indicating the duration for model operation.
  * `datasize`: The size of the data to be processed.

[^Pathak2018]: Jaideep Pathak et al. "Hybrid Forecasting of Chaotic Processes: Using Machine Learning in Conjunction with a Knowledge-Based Model" (2018).
