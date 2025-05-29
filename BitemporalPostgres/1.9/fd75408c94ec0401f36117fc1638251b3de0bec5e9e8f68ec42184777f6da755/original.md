delete_component!(r::T, w::Workflow)  where {T<:ComponentRevision}

  * deletes a component if it was created for the current version or
  * mark its latest component revision as invalid
