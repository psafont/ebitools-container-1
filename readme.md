# How to use

1. Clone this repository
2. Build the image with `docker build -t image_name .`
3. Run the container with `docker run image_name ncbiblast_lwp.pl --email docker@ebi.ac.uk --stype protein --database uniprotkb_swissprot --program blastp sp:wap_rat`
4. Alternatively, to save results it can be run as `docker run --rm -w /results -v /path/local/destination:/results image_name ncbiblast_lwp.pl --email docker@ebi.ac.uk --stype protein --database uniprotkb_swissprot --program blastp sp:wap_rat`

# How to update clients

1. Add the jdispatcher clients' repo as a remote: `git remote add -f -t master --no-tags clients git@github.com:ebi-wp/webservice-clients.git`
2. Load the remote repo's master branch: `git checkout clients/master`
3. Remove everything from the branch except the folder with perl clients: `git subtree split -P perl/lwp -b perl_clients`
4. Go back to master branch: `git checkout master`
5. Insert the modified branch into master: `git subtree add --squash -P clients perl_clients`
6. Clean up the branch: `git branch -D perl_clients`

## Quick guide for the new tools, Hmmer3 phmmer & hmmscan
**How to use the clients**

How to use hmmer3 hmmscan :
> To use the client directly (without Docker) :
>> single sequence input 
```
./clients/hmmer3_hmmscan_lwp.pl --email yours@email.ac.uk --hmmDatabase Pfam ./sequence/single.seq
```
>> more than a sequence input (FASTA format)
```
./clients/hmmer3_hmmscan_lwp.pl --email yours@email.ac.uk --hmmDatabase Pfam --multifasta ./sequence/multi.seq
```
> With Docker :
```
docker run image_name hmmer3_hmmscan_lwp.pl --email yours@email.ac.uk --hmmDatabase Pfam ./sequence/single.seq
```

How to use hmmer3 phmmer :
> To use the client directly (without Docker) :
>> single sequence input 
```
./clients/hmmer3_phmmer_lwp.pl --email yours@email.ac.uk --seqdb uniprotkb ./sequence/single.seq
```
>> more than a sequence input (FASTA format)
```
./clients/hmmer3_phmmer_lwp.pl --email yours@email.ac.uk --seqdb swissprot --multifasta ./sequence/multi.seq
```

> With Docker :
```
docker run image_name ./clients/hmmer3_phmmer_lwp.pl --email yours@email.ac.uk --seqdb uniprotkb ./sequence/single.seq
```

The recent retired tool :
>  ~~hmmer_hmmscan~~ 
