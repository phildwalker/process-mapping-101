This book aims to capture what I have been learning about process mining/ process mapping. The hope is that I can make it digestable to others and use this as a way of capturing what i've worked on before

The book is going to be hosted on netlify and linked to this github repo. You can view it as it gets built out at: https://process-mapping-101.netlify.com/


------- notes ------

Process Sciences // Process Mining // Process Models

Process mining research starting at TU/e (Eindhoven University of Technology) in 1999
	-- In general the field is tied to the growth in big data >> automated creation of event logs


useful terminology

---describing a process--
	deadlock: a path deadlocks if it reaches a non-final state without any outgoing transitions
	livelock: some transitions are still enabled but it is impossible to reach one of the final states
	concurancy
	activity: well defined step in a process (often an event in a event log)
	case: process instance
	trace: the combination of activities into cases (multiple traces make up the process flow)
	resource: person/device executing the activity
	timestamp: crucial element of event logs
	
	desire line/ golden path
	
---process model types---
	transition systems
		consists of states and transitions
		also called a labelled transition system 
			which is a tuple (finite list of ordered elements)
				typical uses of labels include representing input expected, conditions that must be true to trigger the transition/actions performed during the transition, then the end state
		a path terminates successfully if it ends in one of the final states
		a path deadlocks if it reaches a non-final state without any outgoing transitions
	
		transition systems are simple but have problems expressing concurrency succinctly
			example of n parallel activities:
				there are n! possible execution sequences
				the transition system requires 2^n states and n X 2^(n-1) to be able to capture this (often this is called state explosion)
					ie if there 10 parallel activities:
						10! = 3,628,800 possible execution sequences
						2^10 = 1024 reachable states
						10x2^(10-1) = 5120 transitions
						
					on the other hand a petri net needs only 10 transitions and 10 places to model the 10 parallel activities
						while transition systems are foundational, with the concurrent nation of business processes, more expressive models like petri nets are needed to adequately represent process mining results.
	
	petri net
		usage of tokens
		transitions
			must be enabled for a action to occur (also called firing)
		marking >> state of the transaction
		
		contains places (represented as circle) and transitions (represented as a square) and may be connected with 
			places symbolize states/conditions/resources that need to be met/available before an action can be carried out
			transitions symbolize actions
				often we say that one transition fires at a time
		
		there are only "AND" (split/join) and "XOR" (split/join)
		
		a transition is represented as a "box" within a petri net model
		
		often reachability and coverability graphs are created to help show how items move... often they get too big and complicated with "real-life" processes
			if there are 'n' components then the reachability graph has size 2^n
		
		k-bounded: the max number of tokens any state could contain
		safe: a marked petri net is safe it and only iff it is 1-bounded (ie no place holds more than 1 token)
		
	BPMN models (Business Process Management)
	
	there are many different process modeling languages
		transition systems, petri nets, BPMN, C-nets, EPCs, YAWL
			BPMN model, BPEL model, UML activity diagram 
			Workflow Pattern Initiatives 
	
-- process discovery algorithms ---
	alpha algorithms
		builds out a petri net from the event log
	
	
	
	
what is "event data"
	contains a couple of key elements
		activity: well defined step in a process (often an event in a event log)
		case: process instance
		trace: the combination of activities into cases (multiple traces make up the process flow)
		resource: person/device executing the activity
		timestamp: crucial element of event logs
	
	
	couple of useful but not necessary elements

------------
Examples of use of process mingn
	-- analyzing treatment process in hospitals
	-- improving customer services process in a multinational corporation
	-- understanding browsing behavior of customers on a online booking site
	-- analyzing failures of a baggage handling system
	
	
Answering questions like:
	-- what are the most frequent paths in my process? Do they change over time?
	-- what do the cases that take longer than 3 months have in common? where are the bottlenecks causing these delays?
	-- which cases deviate from the reference process? do these deviations also cause delays?

	>> Generally are either performance or conformance related questions
		> performance: response times, service levels







