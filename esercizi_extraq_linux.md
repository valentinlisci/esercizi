#ESERCIZI EXTRA

TOUCH
 Illustrare almeno 2 casi in cui il comando touch può generare una condizione di errore.

Quando non abbiamo i permessi:
touch   /root/filet.xt
permission denied 

quando la cartella in cui vogliamo creare il file non esiste:
touch /paperino/file.txt
---------------------------------------------------------------------------------------------------------------
Numero Processi
Contare il numero totale di processi attualmente in esecuzione sulla propria macchina senza utilizzare utility 
interattive come "top".

ps -e -o stat= | grep -c ‘R’

*-o stat=* stato del processo
*grep -c ‘R’* conta solo quelli con stato R ovvero running 
---------------------------------------------------------------------------------------------------------------
Kernel Version
Trovare il modo (o più modi) per capire se il Kernel attualmente running è il più recente installato sulla macchina. 
Scrivere uno script che esegua automaticamente il controllo e risponda TRUE/FALSE.

controllare la versione del kernel: uname-r 
Aggiornare il kernel: sudo apt dist-upgrade
 
SCRIPT:#!/bin/bash
	
	attuale=$(uname -r)
	echo “kernel: $attuale”

	disponibile=$(apt-cache policy linux-image-generic | grep “candidate”)
	echo “$disponibile”
	
	if  [ “attuale” == “disponibile” ]; then
		echo “true”
	else
		echo “folse”
fi

