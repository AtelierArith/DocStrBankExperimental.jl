```
run_qa_evals(qa_item::QAEvalItem, ctx::RAGResult; verbose::Bool = true,
			 parameters_dict::Dict{Symbol, <:Any}, judge_template::Symbol = :RAGJudgeAnswerFromContext,
			 model_judge::AbstractString, api_kwargs::NamedTuple = NamedTuple()) -> QAEvalResult
```

Evaluates a single `QAEvalItem` using RAG details (`RAGResult`) and returns a `QAEvalResult` structure. This function assesses the relevance and accuracy of the answers generated in a QA evaluation context.

# Arguments

  * `qa_item::QAEvalItem`: The QA evaluation item containing the question and its answer.
  * `ctx::RAGResult`: The RAG result used for generating the QA pair, including the original context and the answers. Comes from `airag(...; return_context=true)`
  * `verbose::Bool`: If `true`, enables verbose logging. Defaults to `true`.
  * `parameters_dict::Dict{Symbol, Any}`: Track any parameters used for later evaluations. Keys must be Symbols.
  * `judge_template::Symbol`: The template symbol for the AI model used to judge the answer. Defaults to `:RAGJudgeAnswerFromContext`.
  * `model_judge::AbstractString`: The AI model used for judging the answer's quality.  Defaults to standard chat model, but it is advisable to use more powerful model GPT-4.
  * `api_kwargs::NamedTuple`: Parameters that will be forwarded to the API endpoint.

# Returns

`QAEvalResult`: An evaluation result that includes various scores and metadata related to the QA evaluation.

# Notes

  * The function computes a retrieval score and rank based on how well the context matches the QA context.
  * It then uses the `judge_template` and `model_judge` to score the answer's accuracy and relevance.
  * In case of errors during evaluation, the function logs a warning (if `verbose` is `true`) and the `answer_score` will be set to `nothing`.

# Examples

Evaluating a QA pair using a specific context and model:

```julia
qa_item = QAEvalItem(question="What is the capital of France?", answer="Paris", context="France is a country in Europe.")
ctx = RAGResult(source="Wikipedia", context="France is a country in Europe.", answer="Paris")
parameters_dict = Dict("param1" => "value1", "param2" => "value2")

eval_result = run_qa_evals(qa_item, ctx, parameters_dict=parameters_dict, model_judge="MyAIJudgeModel")
```
