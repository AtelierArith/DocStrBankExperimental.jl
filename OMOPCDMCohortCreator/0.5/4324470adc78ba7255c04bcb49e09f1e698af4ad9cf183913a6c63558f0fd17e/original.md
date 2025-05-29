GetDrugAmounts(drug*concept*ids; tab = drug_strength)

Return SQL statement that gets the `amount_value` for a given list of `drug_concept_id`'s

# Arguments:

  * `drug_concept_ids` - list of `drug_concept_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the drug*strength table; default `drug*strength`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:drug_concept_id` and `:amount_value`
