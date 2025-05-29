Transform labels back to their unstandardize form. Returns

labels.*transpose(hcat(scale)) .+ transpose(hcat(pivot))
