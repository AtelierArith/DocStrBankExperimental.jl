```
tess_pipeline_tsv(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

Generate a tsv file from the pipeline and save it to the specified file.  Returns `false` if there is a problem adding the tsv generator to the output.

**Arguments:**

| T   | Name     | Default | Description                          |
|:--- |:-------- |:------- |:------------------------------------ |
| R   | pipe     |         | The pipline to collect the tsv from. |
| R   | filename |         | The file to write the tsv to.        |

**Details:**

If the file exists it will be overwritten.

**Examples:**

```jldoctest; filter = r"(\s+)"
using Tesseract

# Generate some pages to load.
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # Make sure we have the data files.

instance = TessInst()
pipeline = TessPipeline(instance)

tess_pipeline_tsv(pipeline, "My Book.tsv")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.tsv")[1:10]
    println(line)
end

# output

level	page_num	block_num	par_num	line_num	word_num	left	top	width	height	conf	text
1	1	0	0	0	0	0	0	500	600	-1
2	1	1	0	0	0	10	9	479	514	-1
3	1	1	1	0	0	11	9	406	14	-1
4	1	1	1	1	0	11	9	406	14	-1
5	1	1	1	1	1	11	9	14	11	95.791931	No
5	1	1	1	1	2	35	12	22	8	95.791931	one
5	1	1	1	1	3	66	9	39	11	92.953789	would
5	1	1	1	1	4	115	9	30	11	92.953789	have
5	1	1	1	1	5	155	9	62	11	96.819153	believed
```

See also: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_pdf`](@ref)           [`tess_pipeline_text`](@ref)
