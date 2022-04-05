Steps to execute twitter tgn code

1. Python 
	
	Version >= 3.7 (3.8 preffered)

2. Dependencies

	pandas==1.1.0
	torch==1.6.0
	scikit_learn==0.23.1

	all versions not vailable plainly with pip, requires manual selection on conda gui

3. Download dataset

	link for wikipedia dataset: 	http://snap.stanford.edu/jodie/wikipedia.csv

4. Dataset location
	
	please store dataset in "data/", replacing "open me.txt"

5. Self-supervised learning using link prediction task

	run the following command in main folder you've stored files in

	python train_self_supervised.py --use_memory --prefix tgn-attn --n_runs 10  
		#command set to default for wikipedia database

6. Supervised learning on dynamic node classification
	
	run the following command in main folder you've stored files in

	python train_supervised.py --use_memory --prefix tgn-attn --n_runs 10
		#command set to default for wikipedia database
		#requires trained model obtained from step 5

7. Baselines to compare tgn to

	# Jodie
	python train_self_supervised.py --use_memory --memory_updater rnn --embedding_module time --prefix jodie_rnn --n_runs 10

	# DyRep
	python train_self_supervised.py --use_memory --memory_updater rnn --dyrep --use_destination_embedding_in_message --prefix dyrep_rnn --n_runs 10