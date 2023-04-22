
from fnmatch import translate
import speech_recognition as sr
from googletrans import Translator

def listen():
    r= sr.Recognizer()

    with sr.Microphone()as source:
        print("listining....")
        r.pause_threshold =1
        audio= r.listen(source,0,8)
    

    try:
        print("recognizing.....")
        query= r.recognize_google(audio,language="hi")
    
    except:
      return""
    
    query= str(query).lower()
    return query 
listen()

print(listen())

def TranslationHinToEng(Text):
    line =str(Text)
    tanslate=Translator()
    result= translate.translate(line)
    data=result.text
    print(f"you : {data}.")
    return data 


def MicExecutation():
    query= listen()
    data = TranslationHinToEng(query)
    return data 
MicExecutation()
--->
