# Movies-ETL process and consolidating into a function

In this module I showcase how to perform ETL on movie data from 3 separate data sources, we went through the data by using ETL methods: inspect, plan, execute repeatedly.  Finally joining the data together and load it into the database for further analysis.  

I consolidated the progression and techniques into a python function that will take 3 files as variables then perform ETL with result into a sql database.  

## Assumptions and limitations:
- `path` is hard coded in `file_dir`
- postgres db is used and heed associated syntax and requirements
  - Database information is hardcoded in `db_string` and function's load section (will load into table named _Challenge8TL_)
  - `db_password` is required and loaded from `config.py`
- Function will take variables `wiki_file, kaggle_file,` and `ratings_file` and perform ETL into database.
  - The 3 variable should be files that uses similar format, integrity, and type: `wiki_file` from wikipedia and as json, `kaggle_file` and `ratings_file` from kaggle and as csv.
  - The files obtained from kaggle should be based on TMDB and ratings of movies.  
  - Function only works on **movies**, meaning data having `imdb_link` and no `No. of episodes` and must have `Director` or `Directed by`
  - Data columns must have at least 90% or more field values, otherwise the column is dropped.  
  - Ratings are merged into the file database table, so they must have `imdb_id` as keys
  - Some data corruption from source were experienced during this code writing, so we will drop movies that match this criteria (wiki release date >1996/01/01 and kaggle release date 1965/01/01)
  - Source data must be within reason to be similar to have assumed columns.  
  - This list of limitation is not exhaustive, for further details see actual code and comments.  
