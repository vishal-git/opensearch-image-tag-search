### Image Tag Search using OpenSearch

The main goal of this repository is to demonstrate how to perform evals for searching images using OpenSearch.

There are two ways to perform image search based on the tags that are contained within those images. 

1. Capture image tags (using a ML model) and then perform a text search to find images, and 
2. Calculate an image embedding vector for each image and then perform image search using text-image similarity.

For option #1, we can use the in-built ML models that are available in Open Search. For option #2, there are two ways: (a) upload a custom model based on the approach described on [this](https://opensearch.org/docs/latest/ml-commons-plugin/custom-local-models/) link, or (b) create image embeddings, as well as text embeddings for the search keyword, _outside_ of OpenSearch. I tried approach (a), but couldn't get it to work. 


In this reposiroty, I have demonstrated options (1) and (2.a). 

#### Image Search using Text Embeddings

The idea is to use the list of image tags as a string and convert it into a text embedding. Then we use the same model to convert the search keyword (e.g., "dog") to a text embedding vector, and perform search to capture relevant images.

Follow notebooks `01` thru `03` to understand how to perform image search using text embeddings. 

* [00_load_data.ipynb](./notebooks/00_load_data.ipynb)
In this notebook, we load a small subset of the Visual Genome dataset.
* [01_prepare_opensearch.ipynb](./notebooks/01_prepare_opensearch.ipynb)
We set up OpenSearch and get it ready for search.
* [02_index_tags_data.ipynb](./notebooks/02_index_tags_data.ipynb)
We ingest the Visual Genome dataset that we created in the first notebook.
* [03_search_and_eval.ipynb](./notebooks/03_search_and_eval.ipynb)
In this Notebook, we perform multiple searches and collect the results to calculate accuracy metrics such as precision and recall.

##### Image Search using Image-Text Embeddings

* [04_image_embeddings.ipynb](./notebooks/04_image_embeddings.ipynb)
In this notebook, we use CLIP model to generate image embeddings and store them in an OpenSearch index. Then we perform search (like we did in the previous notebook and perform evaluation using a judgement dataset.
