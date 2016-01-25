# Music-Decades-Top-100

A sample analysis of music across decades using this dataset is described in the R Markdown file titled, “MusicDecades.Rmd”. The results are shown in the “MusicDecades.pdf” file. 

This README file consists of the following sections:

I   - SOURCES AND LICENSING INFORMATION
II  - CITATION INFORMATION
III - DESCRIPTION OF THE DATASET
IV  - HOW THE DATASET WAS CREATED

I - SOURCES AND LICENSING INFORMATION:
This is a dataset consisting of audio attributes for 600 songs. These are the top 100 hit songs from six decades: 1950s, 1960s, 1970s, 1980s, 1990s, and 2000-2009. The data represents derived work collected from two sources - tsort.info/music/ and the Echo Nest database (http://the.echonest.com/). 

tsort.info is a comprehensive site that uses 130 music charts as its sources for aggregating information about hit songs. The Echo Nest database (now acquired by Spotify) was used to query and obtain information on each song for 13 audio/acoustic attributes.

Please refer to the license.txt file for more information on using this dataset. This dataset is made available by Naresh N. Vempala under a Creative Commons Attribution 4.0 License for free use and distribution. For any commercial use, please consult tsort.info and the Echo Nest. 

II - CITATION INFORMATION:
Please cite Naresh N. Vempala using the DOI for this project, when using the dataset for your analyses and/or publications.


III - DESCRIPTION OF THE DATASET:
The actual dataset is provided in the NVDecades.csv file. The dataset consists of attributes for 600 songs, which are the top 100 hit songs from six decades: 1950s, 1960s, 1970s, 1980s, and 2000-2009. 

Each song has the following attributes. Attributes 4 through 16 are Echo Nest’s attributes. So, please refer to Echo Nest’s documentation and forums for more information on how Echo Nest defines, interprets, and computes these attributes:

1. artist_id - Obtained from the Echo Nest database.

2. artist_name

3. id - The song ID obtained from the Echo Nest database (Note: The same song can have multiple sources. The specific ID used for this song identifies the unique source/version of the song used in this dataset.)

4. key - The key that the Echo Nest believes the song is in. Key signatures start at 0 (C) and ascend the chromatic scale. In this case, a key of 1 represents a song in D-flat.

5. energy - A number that ranges from 0 to 1, representing how energetic The Echo Nest thinks this song is. More information is available here: http://developer.echonest.com/acoustic-attributes.html

6. liveness - Detects the presence of an audience in the recording. More information is available here: http://developer.echonest.com/acoustic-attributes.html

7. tempo - Represents the BPM of the song

8. speechiness - Detects the presence of spoken words in a track. More information is available here: http://developer.echonest.com/acoustic-attributes.html

9. acousticness - The likelihood a recording was created by solely acoustic means such as voice and acoustic instruments as opposed to electronically synthesized instruments. More information is available here: http://developer.echonest.com/acoustic-attributes.html

10. instrumentalness

11. mode - Number representing whether the song is in a minor (0) or major (1) key.

12. time_signature - Time signature of the key; how many beats per measure.

13. duration - Length of the song, in seconds.

14. loudness - The overall loudness of a track in decibels (dB).

15. valence - Indicates how pleasant or positive a song feels.

16. danceability - Describes how suitable a track is for dancing using a number of musical elements (the more suitable for dancing, the closer to 1.0 the value). The combination of musical elements that best characterize danceability include tempo, rhythm stability, beat strength, and overall regularity.

17. title - Title of the song.

18. decade - Identifies which of the six decades the song belongs to.


IV - HOW THE DATASET WAS CREATED:
If you plan on building your own dataset, you might find this section helpful. 
The dataset was created in three steps.

Step 1: The list of 600 song titles with corresponding artist names and decades was obtained from tsort.info/music/. The Echo Nest IDs for all the songs were obtained by querying Echo Nest (You will need a developer account for this). All the song IDs were saved in a csv file. In some cases, apostrophes and commas had to be removed from song titles and artist names while querying and saving to avoid interfering with the csv formatting.

Step 2: Each song was queried by its Echo Nest Song ID to obtain audio attributes from the Echo Nest database in JSON format using R. Be aware of rate limit errors outputting a “429 Too Many Requests” message, since Echo Nest limits the number of queries within short time spans (a few seconds to a minute).

Step 3: Attributes from all 600 songs acquired in Step 2 were merged into one csv file using R. The data was cleaned by removing unnecessary columns (e.g. version, code, status, audio-summary.analysis-url etc.). Original column header names from Echo Nest were replaced with simpler names, and an additional “decades” column was added.
