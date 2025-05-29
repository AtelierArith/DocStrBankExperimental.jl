GetDrugConcepts(drug*exposure*ids; tab = drug_exposure)

Return SQL statement that gets the `drug_concept_id` for a given list of `drug_exposure_id`'s

# Arguments:

  * `drug_exposure_ids` - list of `drug_exposure_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the drug*exposure table; default `drug*exposure`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:drug_exposure_id` and `:drug_concept_id`
