#section for loading all words or specific parts of speech

def load_words():
    with open('words_alpha.txt') as word_file:
        valid_words = list(word_file.read().split())

    return valid_words

def load_nouns():
    with open('91K_nouns.txt') as word_file:
        valid_words = list(word_file.read().split())
        
    return valid_words

def load_verbs():
    with open('31K_verbs.txt') as word_file:
        valid_words = list(word_file.read().split())
        
    return valid_words

def load_adverbs():
    with open('6K_adverbs.txt') as word_file:
        valid_words = list(word_file.read().split())
        
    return valid_words

def load_adjectives():
    with open('28K_adjectives.txt') as word_file:
        valid_words = list(word_file.read().split())
        
    return valid_words

import numpy as np
import random as r

def most_likely_next(typ):
    translate = {"noun":0,
                "adjective":1,
                "verb":2,
                "adverb": 3,
                "conjunction":4,
                "possessive":5,
                "articles":6,
                "none": 4}
    # HMM array for types of words 
    array = np.array([[0, 0, 0.33, 0.41,0.0825,0.0825,0.0825],
                     [0.75,0.15, 0, 0, 0, 0.1, 0],
                     [0, 0.15, 0, 0.5, 0.113, 0.113, .113],
                     [0, 0, 0.75, 0.1, 0, 0, 0], 
                     [0.143,0.143,0.143,0.143,0.143,0.143,0.143], 
                     [0.9, 0.05, 0.05, 0, 0, 0, 0], 
                     [0.8, 0.2, 0, 0, 0, 0, 0]])
    
    array2 = np.array([0.143,0.143,0.143,0.143,0.143,0.143,0.143])
    ctype = translate[typ]
    
    next_pos = r.choices(["noun", "adjective", "verb", "adverb", "conjunction", "possessive", "articles"], array[ctype], k=1)  
    return next_pos


def generate_poem(nouns, verbs, adverbs, adjectives, length):
    #generates a poem based on a list of words, randomly adds conjunctions
    
    #extra lists of pos
    conjunctions = ["after", "although", "as", "as long as", "as much as", "and", "as though", "but",
                   "because", "before","even if", "even though", "if", "in case", "once", "only if", 
                   "since", "than", "that", "though", "till", "unless", "until", "when", "whenever", 
                   "where", "while", "whenever", "or", "for", "yet", "so"]

    possessive = ["his", "her", "their", "my", "your", "its", "our", "whose"]
    
    articles = ["the", "a", "one"]
    
    #init
    poem = ""
    line= ""
    prev = "none"
    
    for i in range(length):
        word = most_likely_next(prev)
        word = str(word[0])
        if len(line) < 50:    
            if word == "noun":
                poem = poem + nouns[r.randint(0,len(nouns)-1)] + " "
                line = line + nouns[r.randint(0,len(nouns)-1)] + " "
                prev = "noun"
            elif word == "adjective":
                poem = poem + adjectives[r.randint(0,len(adjectives)-1)] + " "
                line = line + adjectives[r.randint(0,len(adjectives)-1)] + " "
                prev = "adjective"
            elif word == "verb":
                poem = poem + verbs[r.randint(0,len(verbs)-1)] + " "
                line = line + verbs[r.randint(0,len(verbs)-1)] + " "
                prev = "verb"
            elif word == "adverb":
                poem = poem + adverbs[r.randint(0,len(adverbs)-1)] + " "
                line = line + adverbs[r.randint(0,len(adverbs)-1)] + " "
                prev = "adverb"
            elif word == "conjunction":
                poem = poem + conjunctions[r.randint(0,len(conjunctions)-1)] + " "
                line = line + conjunctions[r.randint(0,len(conjunctions)-1)] + " "
                prev = "conjunction" 
            elif word == "possessive":
                poem = poem + possessive[r.randint(0,len(possessive)-1)] + " "
                line = line + possessive[r.randint(0,len(possessive)-1)] + " "
                prev = "possessive"
            elif word == "articles":
                poem = poem + articles[r.randint(0,len(articles)-1)] + " "
                line = line + articles[r.randint(0,len(articles)-1)] + " "
                prev = "articles"
            else:
                print("Doesn't recognize word")
        else:               
            poem = poem + "\n"
            line = ""
            if word == "noun":
                poem = poem + nouns[r.randint(0,len(nouns)-1)] + " "
                line = line + nouns[r.randint(0,len(nouns)-1)] + " "
                prev = "noun"
            elif word == "adjective":
                poem = poem + adjectives[r.randint(0,len(adjectives)-1)] + " "
                line = line + adjectives[r.randint(0,len(adjectives)-1)] + " "
                prev = "adjective"
            elif word == "verb":
                poem = poem + verbs[r.randint(0,len(verbs)-1)] + " "
                line = line + verbs[r.randint(0,len(verbs)-1)] + " "
                prev = "verb"
            elif word == "adverb":
                poem = poem + adverbs[r.randint(0,len(adverbs)-1)] + " "
                line = line + adverbs[r.randint(0,len(adverbs)-1)] + " "
                prev = "adverb"
            elif word == "conjunction":
                poem = poem + conjunctions[r.randint(0,len(conjunctions)-1)] + " "
                line = line + conjunctions[r.randint(0,len(conjunctions)-1)] + " "
                prev = "conjunction" 
            elif word == "possessive":
                poem = poem + possessive[r.randint(0,len(possessive)-1)] + " "
                line = line + possessive[r.randint(0,len(possessive)-1)] + " "
                prev = "possessive"
            elif word == "articles":
                poem = poem + articles[r.randint(0,len(articles)-1)] + " "
                line = line + articles[r.randint(0,len(articles)-1)] + " "
                prev = "articles"
            else:
                print("Doesn't recognize word")
            
    return poem

nouns = load_nouns()
verbs = load_verbs()
adverbs = load_adverbs()
adjectives = load_adjectives()
                       

print(generate_poem(nouns, verbs, adverbs, adjectives, 30))
